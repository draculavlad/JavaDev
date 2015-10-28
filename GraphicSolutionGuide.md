# Graphic Solution GUIDE#

## Resizing##
* Dependency of Resizing Tools Simple Image
```xml
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>simpleimage</artifactId>
      <version>1.2.3</version>
    </dependency>
    <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
      <version>2.6</version>
    </dependency>

    <dependency>
      <groupId>commons-logging</groupId>
      <artifactId>commons-logging</artifactId>
      <version>1.1.1</version>
    </dependency>
    <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
      <version>2.4</version>
    </dependency>
    <dependency>
      <groupId>javax.media</groupId>
      <artifactId>jai-core</artifactId>
      <version>1.1.3</version>
    </dependency>
    <dependency>
      <groupId>com.sun.media</groupId>
      <artifactId>jai-codec</artifactId>
      <version>1.1.3</version>
    </dependency>
  </dependencies>

  <repositories>
    <repository>
      <id>jboss-3rd-party-releases</id>
      <url>https://repository.jboss.org/nexus/content/repositories/thirdparty-releases/</url>
    </repository>
  </repositories>
```

* Usage
```java
import java.io.File;
  import java.io.FileInputStream;
  import java.io.FileOutputStream;

  import org.apache.commons.io.IOUtils;

  import com.alibaba.simpleimage.render.ReadRender;
  import com.alibaba.simpleimage.render.ScaleParameter;
  import com.alibaba.simpleimage.render.ScaleRender;
  import com.alibaba.simpleimage.render.WriteParameter;
  import com.alibaba.simpleimage.render.WriteRender;

  File in = new File("/source.jpg");      //原图片
  File out = new File("/dest.jpg");       //目的图片
  ScaleParameter scaleParam = new ScaleParameter(false, 1024, 1024);  //将图像缩略到1024x1024以内，不足1024x1024则不做任何处理
  WriteParameter writeParam = new WriteParameter();   //输出参数，默认输出格式为JPEG

  FileInputStream inStream = null;
  FileOutputStream outStream = null;
  ImageRender wr = null;
  try {
      inStream = new FileInputStream(in);
      outStream = new FileOutputStream(out);
      ImageRender rr = new ReadRender(inStream);
      ImageRender sr = new ScaleRender(rr, scaleParam);
      wr = new WriteRender(sr, outStream, writeParam);

      wr.render();                            //触发图像处理
  } catch(Exception e) {
      e.printStackTrace();
  } finally {
      IOUtils.closeQuietly(inStream);         //图片文件输入输出流必须记得关闭
      IOUtils.closeQuietly(outStream);
      if (wr != null) {
          try {
              wr.dispose();                   //释放simpleImage的内部资源
          } catch (SimpleImageException ignore) {
              // skip ... 
          }
      }
  }
```

## Alter Resolution ##
