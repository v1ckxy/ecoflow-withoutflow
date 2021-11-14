# ecoflow-iot-reverse
Trying to understand how to communicate with Ecoflow Portable Power Stations

## Initial considerations

- Device cannot be reset to "factory settings".

- The ip of an Ecoflow Delta Max in offline mode is 192.168.4.1

## Known open ports:
* 80
* 6093
* 8055

If you do an aggressive port scan with nmap (as soon as you touch port 6093, for example), it will exit offline mode.

- On port 80 there's a http server where can change the wifi connection parameters. 
If you delete the SSID, password and save, it will no longer connect to the internet.

- If you make a connection to port 6093, the device will return to IOT (online) mode.

- The app communicates with the device via byte-stream to port 8055.

- If you do an aggressive port scan with nmap (or touch port 6093), it will exit offline mode.


## Communication with device
Classes that a priori take care of communication with the device from the app in offline mode:

### com.ecoflow.common.utils.StreamUtils
- public static void closeStream(Closeable paramCloseable)
- public static String[] convertStringToArray(String paramString, char paramChar)
- public static byte[] getBytesFromStream(InputStream paramInputStream)
- public static byte[] getBytesFromStream(InputStream paramInputStream, int paramInt)
- public static int stringToInt(String paramString)

### com.ecoflow.common.utils.ByteUtils
- public static byte[] File2byte(File paramFile)
- public static byte[] addBytes(byte[] paramArrayOfbyte1, byte[] paramArrayOfbyte2)
- public static byte bitToByte(byte[] paramArrayOfbyte)
- public static int bytes2Uint16(byte[] paramArrayOfbyte)
- public static int bytes2Uint32(byte[] paramArrayOfbyte)
- public static int bytes2Uint8(byte[] paramArrayOfbyte)
- public static int bytes4ArrraystoInt(byte[] paramArrayOfbyte)
- public static String bytesToHex(byte[] paramArrayOfbyte)
- public static int bytesToInt(byte[] paramArrayOfbyte, int paramInt)
- public static int bytesToInt2(byte[] paramArrayOfbyte, int paramInt)
- public static int convertByteToInt(byte paramByte)
- public static int getBit(byte paramByte, int paramInt)
- public static String getBitForLog(byte paramByte)
- public static int getBits(byte paramByte, int paramInt1, int paramInt2)
- public static byte[] getCrc16(byte[] paramArrayOfbyte)
- public static float getFloat(byte[] paramArrayOfbyte)
- public static byte[] getRunOnceDate(Date paramDate)
- public static short getShort(byte[] paramArrayOfbyte, int paramInt)
- public static byte[] getTRtcHalData(Date paramDate)
- public static int getUint16(int paramInt)
- public static int getUint32(int paramInt)
- public static short getUint8(short paramShort)
- public static byte[] hexStringToBytes(String paramString)
- public static byte[] intToBytes2(int paramInt)
- public static byte[] intToUint16(int paramInt)
- public static byte[] intToUint32(int paramInt)
- public static byte[] intToUint8(int paramInt)
- public static float toFloat(byte[] paramArrayOfbyte)
- public static String toHexStringForLog(byte[] paramArrayOfbyte)
- public static int toSignInt(byte[] paramArrayOfbyte)
- public static int toSignedInt(byte[] paramArrayOfbyte)
- public static int toUnsignedInt(byte paramByte)
- public static int toUnsignedInt(byte[] paramArrayOfbyte)

### com.ecoflow.iot.bean.socket
- public class FrameInfo
- public byte[] getAck_type()
- public byte[] getCheck_type()
- public byte[] getCmd_func()
- public byte[] getCmd_id()
- public int getData_len()
- public byte[] getDest()
- public byte[] getEnc_type()
- public byte[] getIs_ack()
- public byte[] getIs_queue()
- public byte[] getIs_rw_cmd()
- public byte[] getLdata()
- public byte[] getLink_id()
- public byte[] getNeed_ack()
- public byte[] getPdata()
- public byte[] getProduct_id()
- public byte[] getSeq()
- public byte[] getSrc()
- public byte[] getTime_snap()
- public void setAck_type(byte[] paramArrayOfbyte)
- public void setCheck_type(byte[] paramArrayOfbyte)
- public void setCmd_func(byte[] paramArrayOfbyte)
- public void setCmd_id(byte[] paramArrayOfbyte)
- public void setData_len(int paramInt)
- public void setDest(byte[] paramArrayOfbyte)
- public void setEnc_type(byte[] paramArrayOfbyte)
- public void setIs_ack(byte[] paramArrayOfbyte)
- public void setIs_queue(byte[] paramArrayOfbyte)
- public void setIs_rw_cmd(byte[] paramArrayOfbyte)
- public void setLdata(byte[] paramArrayOfbyte)
- public void setLink_id(byte[] paramArrayOfbyte)
- public void setNeed_ack(byte[] paramArrayOfbyte)
- public void setPdata(byte[] paramArrayOfbyte)
- public void setProduct_id(byte[] paramArrayOfbyte)
- public void setSeq(byte[] paramArrayOfbyte)
- public void setSrc(byte[] paramArrayOfbyte)
- public void setTime_snap(byte[] paramArrayOfbyte)
- public String toString()


