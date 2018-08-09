# learn-stubby4j
เรียนรู้การใช้งาน stubby4j สำหรับ stub web service (เช่น REST)

## Stubby4j คืออะไร
คือ Stub HTTP(s) Server สำหรับทดสอบระบบงานที่ต้องการใช้งาน Web service เช่น REST, WSDL และ SOAP หรือประเภทอื่น ๆ รวมทั้ง service ภายนอกอื่นๆ อีกด้วย

## Quick start
เราจะทดสอบแบบง่ายที่สุดด้วย "Hello world" ก่อนที่จะเริ่ม เตรียมระบบให้พร้อม

### Minimum system requirements ที่จะใช้รัน stubby4j
* version >= 4.0.0: Oracle JRE v1.8.0_60
* version >= 3.0.0: Oracle JRE v1.7.0_76
* version = 2.0.22: Oracle JRE v1.7.0_04
* version < 2.0.22: Oracle JRE 1.6.0_65-b14-462

### จากนั้นทำตามนี้
* ดาวน์โหลด stubby4j เวอร์ชันล่าสุด[ที่นี่](https://search.maven.org)
* สร้างไฟล์ YAML ตามนี้ (สมมติว่าชื่อ `hello.yaml`)

```yaml
-  request:
      method: GET
      url: /hello-world
 
   response:
      status: 200
      headers:
         content-type: application/json
      body: '{"text": "Hello World!"}'
```
* จากนั้นรันด้วยคำสั่ง
```
java -jar stubby4j-x.x.xx.jar -d hello.yaml
```

ผมรันแล้วจะได้ผลลัพธ์ประมาณนี้
```
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
Loaded: [GET] /hello-world

stubby4j successfully started after 1317 milliseconds at 2018-08-09 23:03:44+0700

Admin portal configured at http://localhost:8889
Admin portal status enabled at http://localhost:8889/status
Stubs portal configured at http://localhost:8882
Stubs portal configured with TLS at https://localhost:7443 using internal keystore

Quit: ctrl-c

```

* ลองทดสอบด้วย Postman
![ลองทดสอบด้วย Postman](https://raw.githubusercontent.com/golfz/learn-stubby4j/master/Screenshot-01.png)

