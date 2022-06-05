# Arduino ve LabVIEW ile Sıcaklık Kontrol Uygulaması

LabVıew ve Arduino ile sıcaklık kontrol uygulaması içermektedir. Bu uygulamada LM35 sensöründen alınan veriler LabVIEW' aktarılmıştır.

## Proje Dosyası Hakkında

Arduino kodlarını içermektedir. Serial portla haberleşme sağlanıp Arduino Nano' nun A0 bacağına bağlanan pinden analog okuma yapılır. Serial olarak yazdırılır.

 

## LM35 Sıcaklık Ölçümü Dosyası Hakkında

Projenin VI dosyasını içerir. Front panelde Thermometer gösterge paneli,üç tane gösterge ledi, ikitane numerik kontrol paneli,bir tane port kontrol paneli , bir tane Waveform Chart, bir tane bound rate, bir tane numeric indicator ve bir tane, stop durdurma düğmesi bulunmaktadır. Back panelde VISA haberleşmesi yapılıp döngü içinde daha önceden belirlenen  değerlere göre karşılaştırma yapılmaktadır.



## Images Hakkında

Projenin farklı durumlardaki fotoğrafını içerir.

## Nasıl Çalışır

 Yazdığımız Arduino kodlarını Arduino'ya yüklüyoruz. Serial olarak Arduino ile haberleşme sağlayıp oluşturduğumuz LabVIEW dosyasını açıyoruz. Açılan projede serial port panelinden Arduino'yu bağladığımız COM'u seçmeli ve 'Normal ' ve 'Yüksek ' olarak adlandırılan referans değerlerini belirlemeliyiz.

Arduino'nun A0 pinine bağlı olan LM35 sensöründen okunan değerler VI'daki Thermometer göstergesinden okunabilir ve grafiği yansıltılır. Belirlenen referans değerlerine göre ışık şiddetini ledlerle düşük, normal veya yüksek olarak görebiliriz.
LabVIEW projesini çalıştırmadan önce Serial portta Arduinonun bağlı olduğu COM seçilmeli ve ışık şiddeti referans değerleri yazmamız gerekir.


## Arduino Kodları




int lm35Pin = A0;


int zaman = 50;
int okunan_deger = 0;
float sicaklik_gerilim = 0;
float sicaklik = 0;
void setup()
{

Serial.begin(9600);
}
void loop()
{
okunan_deger = analogRead(lm35Pin);
sicaklik_gerilim = (okunan_deger / 1023.0)*5000;
sicaklik = sicaklik_gerilim /10.0;
Serial.println(sicaklik);
delay (200);
}
