# GraalVM (High Performance. Cloud Native. Polyglot.)

GraalVM нь Java болон бусад JVM хэл дээр бичигдсэн програмуудын гүйцэтгэлийг хурдасгах, мөн JavaScript, Python болон бусад олон алдартай хэлнүүдийн runtime гүйцэтгэх зорилготой өндөр гүйцэтгэлтэй JDK юм. 🚀 GraalVM нь Java програмуудыг ажиллуулах хоёр аргыг санал болгодог: Graal just-in-time (JIT) хөрвүүлэгч бүхий HotSpot JVM дээр эсвэл ahead-of-time (AOT) программ. GraalVM-ийн polyglot чадвар нь олон програмчлалын хэлийг нэг программд ажилуулдаг,

## Running Modes

GraalVM нь JVM runtime environment, Native Image, Java on Truffle (ижил Java програмуудыг аль алинд нь ажиллуулж болно) хэд хэдэн горимыг санал болгодог ажиллах орчинтой гэдгээрээ өвөрмөц юм.

### Native image

Native Image нь Java кодыг бие даасан программ эсвэл native дундын library болгон нэгтгэдэг шинэлэг технологи юм. native executable build хийх явцад боловсруулагддаг Java байт код нь бүх програмын class, dependencies, third party dependent libraries, болон шаардлагатай JDK class-уудыг агуулдаг. Үүсгэсэн бие даасан программ нь JVM шаарддаггүй үйлдлийн систем болон машины архитектур тус бүрд зориулагдсан байдаг. 

### Java on Truffle

Java on Truffle нь Java Virtual Machine Specification-ийн хэрэгжилт бөгөөд Truffle language implementation framework-оор built хийгддэг. Энэ нь бүх үндсэн components-ийг агуулсан, Java Runtime Environment library-тай ижил API хэрэгжүүлдэг, GraalVM-ийн бүх JAR болон native сангуудыг дахин ашигладаг бүрэн Java VM юм.

## GraalVM is good for java | Жава - д үзүүлэх давуу талууд

### 1. Accelerate application performance | Аппын performance - ийг хурдасгах

Better Java application performance out of the box

GraalVM-ийн high performance JIT хөрвүүлэгч нь илүү хурдан ажилладаг оновчтой native machine code - ыг үүсгэдэг, garbage бага гардаг, мөн өндөр түвшний хөрвүүлэгч оновчлол, түрэмгий, боловсронгуй аргуудын ачаар бага CPU ашигладаг.

Эцсийн үр дүн нь cloud болон дэд бүтцийн зардлыг бууруулж, илүү хурдан ажиллаж, бага нөөц зарцуулдаг програмууд юм.

![Speedup vs OpenJDK11](https://www.graalvm.org/resources/img/java/20.3vs11.png)

Хурдны хэмжээ нь ажлын ачааллын төрлөөс хамаарна Renaissance-ийн жишиг иж бүрдэл дээр "орчин үеийн олон төрлийн ажлын ачааллыг агуулсан JVM-д зориулсан төрөл бүрийн түгээмэл систем, хүрээ, программуудаас бүрдсэн”, GraalVM Enterprise нь 1.55 дахин хурдасгаж, OpenJDK 8 болон OpenJDK 11-ийн ижил төстэй үр дүнд хүрдэг.

#### 1.1 Orcale Cloud Infrastructure

[GraalVM Enterprise дээр Oracle Cloud Infrastructure (OCI) Monitoring (телеметрийн) үйлчилгээг](https://blogs.oracle.com/cloud-infrastructure/post/graalvm-powers-oracle-cloud-infrastructure) ажиллуулснаар, transaction боловсруулалтын хурдыг 10%-иар нэмэгдүүлж, хог цуглуулах хугацааг 25%-иар бууруулсан. GC түр зогсоох хугацааг 17% бууруулсан, болон CPU-ийн ашиглалтыг 5% бууруулсан, Эдгээр сайжруулалт нь хэдэн арван сая өгөгдлийн цэгийг тогтмол боловсруулдаг санах ой ихтэй үйлчилгээнд ихээхэн ач холбогдолтой. мөн OCI үйлчилгээний offerings өсөн нэмэгдэж буй цуглуулгаас ирж буй сая сая хүсэлтэд үйлчилдэг.

![OCI Monitoring Service Throughput (transaction per second)](https://www.graalvm.org/resources/img/java/oci_monitoring.png)


### 2. Better performance with no code changes | Кодын өөрчлөлтгүйгээр илүү сайн гүйцэтгэл хийдэг

Run Java 8 and 11 applications with no code changes

GraalVM нь тохирох JDK-г агуулдаг бөгөөд одоогоор Java 8 эсвэл Java 11 дээр суурилсан татан авалтуудыг санал болгож байна. GraalVM-г ашиглан Java програмуудыг хурдасгах, 
Native Image функцээр программуудыг build хийх эсвэл бусад хэл дээрх сангуудыг нэгтгэхийн тулд та OpenJDK-н хамгийн сүүлийн хувилбар руу төвөгтэй шилжилт хийх шаардлагагүй байдаг.
Үйлчилгээг GraalVM руу шилжүүлэх нь ихэвчлэн JDK татан авалт эсвэл үндсэн контейнерийн image GraalVM дээр суурилсан кодоор солих эсвэл шинэ хэлний функцийг ашиглах шаардлагагүй!

### 3. Supported by industry-leading Java application frameworks | Жава гийн алдартай нийтлэг frameworks - уудыг дэмждэг.

Helidon, Micronaut, Quarkus, and Spring Boot

Most major Java application and microservice frameworks are designed with GraalVM Native Image in mind or are working on adding first-class support.

### 4. Lower infrastructure costs | Дэд бүтэцийн зардал бага

Consume less memory and CPU, reducing your cloud computing costs with ahead-of-time compilation for Java microservices

> Oracle GraalVM Enterprise Edition нь манай Dell EMC серверүүдийн гүйцэтгэлийн сонголт байсан. Java ажлын ачааллын шинжилгээ ба SPECjbb®2015 жишиг нь max-jOPS үр дүнг бараг 8%-иар сайжруулсан. 
															- `Kurtis Bowman, Director of Architecture, Server Office of the CTO, Del EMC`

> Үндсэн кодыг өөрчлөхгүйгээр ижил hardware гүйцэтгэлийн 8-11 хувийн сайжруулалтыг харах боломжтой байх нь насан туршдаа нэг удаа тохиох үйл явдал бөгөөд энэ нь Твиттерийн зардлыг ихээхэн хэмнэж, ирээдүйд уян хатан байдлыг бий болгоно.
															- `Chris Thalinger, Staff Software Engineer, Twitter`
### 5. Equally excellent developer productivity | Хөгжүүлэгчийн бүтээмж маш сайн

Fits in your workflow. Works with favorite IDEs debuggers, and other java tools

### 6. Expanding the Java ecosystem | Жава экосистемийг өргөжүүлэх

With GraalVM your Java applications can easily and safely use thousands of Node modules, Python libraries, and even C or C++ LLVM libraries

Java Virtual Machine (JVM) нь жижиг суулгагдсан төхөөрөмжөөс эхлээд mainframe хүртэл бүх зүйл дээр Java програмуудыг ажиллуулах боломжийг олгодог. 
Энэ нь кодыг зөөвөрлөх чадварыг идэвхжүүлэхийн тулд үндсэн hardware болон үйлдлийн системийн платформуудын нарийн ширийн зүйлийг хийсвэрлэн гаргадаг high-performance ажиллах хугацаа юм.
Гэвч JVM нь Java байт кодын завсрын форматаар хөрвүүлсэн програмуудыг ажиллуулдаг тул Java хэлний талаар юу ч мэддэггүй нь харагдаж байна. 
Энэ нь Java байт кодыг хөрвүүлж болох аливаа хэлийг JVM дээр ажиллуулж болно гэсэн үг юм, жишээ нь Scala, Kotlin, Clojure. 
Гэсэн хэдий ч Java байт кодыг хөрвүүлдэггүй олон алдартай хэл байдаг бөгөөд JVM-ийн давуу тал болон цаг тухайд нь эмхэтгэснээр гүйцэтгэлийн давуу талыг ашиглах боломжгүй байдаг.0

Гэвч [`Truffle language implementation framework`](https://www.graalvm.org/22.2/graalvm-as-a-platform/language-implementation-framework/) ачаар GraalVM нь JVM дээр JavaScript/Node.js, Ruby, Python, R зэрэг алдартай програмчлалын хэлүүдийг ажиллуулахад дэмжлэг үзүүлдэг. 
Мөн LLVM бит код эсвэл WebAssembly (Wasm) дээр хөрвүүлсэн C, C++ болон бусад хэлүүдийг дэмждэг. GraalVM болон Truffle нь JVM дээр Java-ийн бус байт код програмуудыг ажиллуулах боломжийг олгодоггүй бөгөөд 
Truffle нь GraalVM дээр ажилладаг Java програмуудын нэгэн адил GraalVM-ийн advanced оновчтой хөрвүүлэгч технологийг ашиглан илүү хурдан бөгөөд хялбар ажиллах боломжийг олгодог.
Бүх тохиолдолд GraalVM Truffle хэл нь JVM дээр анхны ажиллах хугацаандаа ажиллаж байснаас хамаагүй хурдан бөгөөд ихэвчлэн хэд дахин хурдан ажилладаг.

> TruffleRuby нь optcarrot дээрх CRuby-ээс ес дахин хурдан байдаг тул хурдны хувьд өндөр боломжтой. 
																- `Carol Chen, Software Engingeer, Shopify` 

![GraalVM Truffle Languages](https://www.graalvm.org/resources/img/java/TruffleStack.png)

GraalVM нь хэд хэдэн хэл дээр бичигдсэн программуудыг ажиллуулах чадвартайгаас гадна нэгээс олон программуудыг ажиллуулах боломжтой! GraalVM-ийн дэмждэг аль ч хэлээр ашиглаж болох мянга мянган ашигтай Node.js багцууд, Python сангууд болон Java сангууд байдаг.
Энэ нь Python машин сургалтын чадавхийг агуулсан Java микро үйлчилгээ эсвэл статистик өгөгдлийн шинжилгээнд R ашигладаг JavaScript программуудыг ашиглах боломжийг олгодог.

GraalVM-ийн олон хэлний дэмжлэг нь өөр хэл, домэйны мэдлэгтэй хөгжүүлэгчдэд хамтран ажиллах боломжийг олгодог

> R кодыг Scala/JVM төсөлд оруулах нь R-д хандах боломжтой өгөгдөл боловсруулах хүчирхэг багцуудыг ашиглах маш сайн арга байж болох юм… Энэ нь та (эсвэл таны өгөгдөл судлаач) тусгай засварлагч (жишээ нь RStudio) ашиглан өөрийн R талыг үүсгэж болно гэсэн үг юм. функцийг ашиглахын зэрэгцээ та JVM тал дээр өөрийн дуртай засварлагчийг ашиглаж болно (жишээ нь, IntelliJ).	 																				- `Nathan Perdijk, Scala Developer, Codestar`

# Use Cases 

GraalVM технологийг бүтээгдэхүүн, сервисүүддээ амжилттай ашигладаг компаниуд

### Facebook

Facebook платформ нь Java-г big data(Spark, Presto гэх мэт), backend сервис, mobile зэрэг салбарт ашигладаг. GraalVM-д шилжсэнээр ямар ч кодын өөрчлөлтгүйгээр Spark-ийн ажлын ачааллыг 10%-42%-иар хурдасгаж, санах ой болон CPU-ийн хэрэглээг бууруулж чадсан.

### Twitter

Twitter saw GraalVM as an optimizing compiler and JVM, and tried it. Running the Tweet service on GraalVM, Twitter has achieved 8-11% CPU saving while requiring 18% fewer machines.

Twitter нь datacenter-үүддээ ~1000 JVM ажиллуулдаг.  Твиттер GraalVM-ийг optimizing compiler болон JVM нь туршиж үзсэн. GraalVM дээр Tweet үйлчилгээг ажиллуулснаар Twitter нь CPU-ийн 8-11% хэмнэж, 18% цөөхөн машин шаарддаг.

### Standard chartered

Олон улсын банк санхүүгийн компани Standard Chartered Bank нь Java-дээр хөгжүүлэхдээ ихэвчлэн ашигладаг бөгөөд Java application хурдан эхлүүлэх, cloud хэрэглээнд дасан зохицох, CI/CD дамжуулах шугамыг оновчтой болгох арга замыг эрэлхийлсэн. Аппликешнүүдийн гүйцэтгэлийг сайжруулж, тэдгээрийг cloud болгохын тулд инженерийн баг GraalVM Enterprise-г Java runtime-дээр ашиглахыг авч үзсэн.

### Oracle netsuite

NetSuite нь 19,000 гаруй байгууллагад ERP, Санхүү, CRM, цахим худалдаа зэргийг багтаасан cloud-д суурилсан бизнесийн удирдлагын үйлчилгээг үзүүлдэг. Инженерийн баг дараагийн үеийн зөвлөмжийн систем дээрээ ажиллаж байхдаа GraalVM болон grCUDA-г ашигласан бөгөөд одоо байгаа Java application-йи хүрээнд хурдан бөгөөд өндөр нарийвчлалтай машин сургалтын загваруудыг бүтээжээ.

### Alibaba Group

Цахим худалдааны Alibaba компани нь GraalVM-ийн Native Image технологийг ашиглан microservice applications-уудын ELF файлууд руу статик байдлаар хөрвүүлдэг бөгөөд энэ нь Java програмуудын эх кодыг эхлүүлэх хугацааг хурдан болгодог. Тэдний инженерийн баг native image хэлбэрээр эмхэтгэсэн хэд хэдэн SOFABoot програмуудыг байрлуулж, төсөлд үр дүнтэй хувь нэмэр оруулсан.

### Oracle Cloud Infrastructure

Oracle Cloud (OCI) Monitoring service нь одоо GraalVM Enterprise дээр ажиллаж байна. GraalVM-г ашигласнаар Monitoring service нь garbage collection хугацааг 25%, програмыг түр зогсоох хугацааг 17% бууруулж, мөн throughput-ыг 10% нэмэгдүүлсэн. Эдгээр сайжруулалтын үр ашиг нь Oracle Cloud платформ дээр ашиг тус өгж байна.

### Nvidia

GPU-accelerated сангуудыг одоо байгаа програм хангамжийн стекүүдэд нэгтгэх нь ялангуяа өндөр түвшний скрипт хэл дээр бичигдсэн програмуудын хувьд хэцүү байдаг. Truffle language implementation framework дээр бүтээгдсэн grCUDA нь хөгжүүлэгчдэд GPU болон GraalVM хэл (Python, R, Ruby, JavaScript) хооронд өгөгдлийг үр дүнтэй хуваалцах, GPU цөмүүдийг ажиллуулах боломжийг олгодог.

















































