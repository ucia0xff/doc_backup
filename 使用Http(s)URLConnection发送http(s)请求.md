```java

import com.alibaba.fastjson.JSONObject;

import javax.net.ssl.*;
import java.io.BufferedReader;
import java.io.DataOutputStream;
import java.io.InputStreamReader;

import java.net.HttpURLConnection;
import java.net.URL;

public class HttpUtil {

	/**
	 * POST提交json格式的数据
	 * 
	 * @param url
	 *            请求地址
	 * @param param
	 *            提交的数据
	 * @return 返回响应
	 */
	public static JSONObject doPost(String url, JSONObject param) {
		JSONObject res = null;
		if (null == url || url.length() == 0 || null == param) {
			return null;
		}
		if (url.startsWith("https")) {
			res = httpsRequest(url, param);
		} else {
			res = httpRequest(url, param);
		}
		return res;
	}

	/**
	 * 发送http POST请求
	 *
	 * @param url
	 *            请求地址
	 * @param param
	 *            提交的数据
	 * @return
	 */
	private static JSONObject httpRequest(String url, JSONObject param) {
		JSONObject res = null;
		HttpURLConnection conn = null;
		try {
			URL _url = new URL(url);
			conn = (HttpURLConnection) _url.openConnection();
			conn.setRequestMethod("POST");
			conn.setConnectTimeout(6000);
			conn.setReadTimeout(6000);
			conn.setRequestProperty("Content-Type", "application/json");
			conn.setRequestProperty("Charset", "UTF-8");
			conn.setUseCaches(false);
			conn.setDoOutput(true);
			conn.setDoInput(true);
			conn.connect();

			// 提交数据
			DataOutputStream dos = new DataOutputStream(conn.getOutputStream());
			dos.write(param.toString().getBytes());
			dos.flush();
			dos.close();

			// 读取返回内容
			BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream(), "utf-8"));
			StringBuffer response = new StringBuffer();
			String line = null;
			while (null != (line = br.readLine())) {
				response.append(line);
			}
			res = JSONObject.parseObject(response.toString());
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			if (null != conn) {
				conn.disconnect();
			}
		}
		return res;
	}

	/**
	 * 发送https POST请求
	 * 
	 * @param url
	 *            请求地址
	 * @param param
	 *            提交的数据
	 * @return
	 */
	private static JSONObject httpsRequest(String url, JSONObject param) {
		JSONObject res = null;
		HttpsURLConnection conns = null;
		try {
			// 创建SSLContext
			SSLContext sslContext = SSLContext.getInstance("SSL");
			TrustManager[] tm = { new TrustAnyTrustManager() };
			// 初始化
			sslContext.init(null, tm, new java.security.SecureRandom());

			HostnameVerifier ignoreHostnameVerifier = new HostnameVerifier() {
				public boolean verify(String s, SSLSession sslsession) {
					return true;
				}
			};
			// 设置使用的SSLSoctetFactory
			HttpsURLConnection.setDefaultHostnameVerifier(ignoreHostnameVerifier);
			HttpsURLConnection.setDefaultSSLSocketFactory(sslContext.getSocketFactory());

			URL _url = new URL(url);
			conns = (HttpsURLConnection) _url.openConnection();
			conns.setRequestMethod("POST");
			conns.setConnectTimeout(6000);
			conns.setReadTimeout(6000);
			conns.setRequestProperty("Content-Type", "application/json");
			conns.setRequestProperty("Charset", "UTF-8");
			conns.setUseCaches(false);
			conns.setDoOutput(true);
			conns.setDoInput(true);
			conns.connect();

			// 提交数据
			DataOutputStream dos = new DataOutputStream(conns.getOutputStream());
			dos.write(param.toString().getBytes());
			dos.flush();
			dos.close();

			// 读取返回内容
			BufferedReader br = new BufferedReader(new InputStreamReader(conns.getInputStream(), "utf-8"));
			StringBuffer response = new StringBuffer();
			String line = null;
			while (null != (line = br.readLine())) {
				response.append(line);
			}
			res = JSONObject.parseObject(response.toString());
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			if (null != conns) {
				conns.disconnect();
			}
		}
		return res;
	}
}

```