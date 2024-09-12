# SignHub E-İmza Entegrasyon Süreci Dokümanı
 
## 1. Entegrasyon Süreç Tarafları
- **İmza Atacak Kişi**: E-imza işlemini gerçekleştiren son kullanıcı.
- **Entegrasyon Servisi**: Onaylarım SignHub servisleri ile iletişim kurulan servis.
- **Onaylarıım SignHub Servisi**: Sürecin yönetildiği servis.
 
---
 
## 2. Süreç Adımları
 
### 2.1. İmza Atacak Kişi Tarafından Talep
- İmza atacak kişi tarafından e-imza işleminin yapılması talep edilir.
### 2.2. Süreç Başlatma (CreateFlow)
- Entegrasyon servisi, süreci signhub servislerine istek atarak başlatır ve yaratılan sürece bir **FlowID** (Süreç Kimliği) atanır. SignHub servisi atanan FlowID bilgisini Entegrasyon servisine döner.
- SignHub servisi tarafından oluşturulan FlowID, entegrasyon servisi tarafından saklanır.
 
### 2.3. İmzalanacak Dökümanın Eklenmesi
- FlowID ile kullanılarak imzalanacak döküman entegrasyon servisi tarafından signhub servislerine gönderilir.
- Gönderilen dökümanın bilgileri ve PageID (Sayfa Kimliği) signhub servisi tarafından entegrasyon servisine döner. Entegrasyon servisi opsiyonel adımları kullanacaksa PageID bilgilerini saklar*.
 
### 2.4. Gönderilecek Sürece Ek Dökümanlar Ekleme (Opsiyonel)
- İsteğe bağlı olarak, FlowID ile ilişkilendirilen sürece ek dökümanlar eklenebilir.
- PageID ile beraber döküman üzerinde imzaların ve QR kodun bulunacağı alanlar belirlenir.
 
### 2.5. Sürecin Başlatılması
- Entegrasyon servisi saklanan FlowIDsini signhub servisine süreci başlatması için gönderir
- SignHub servisi süreci başlatılır ve imza atacak kişiye imza için açılması gereken URL döner. Bu URL, imzalama işlemi için pop-up olarak kullanıcıya gösterilir.
 
### 2.6. İmzalama İşlemi
- Kullanıcı, açılan imzalama arayüzünde e-imza aracını kullanarak imzalama işlemini gerçekleştirir.
 
### 2.7. Süreç Durumunun Takibi
- Entegrasyon servisi, sürecin durumunu **FlowID** ile takip eder. Bu işlem, scheduled jobs ile belirli aralıklarla yapılır.
- Süreç durumu ve imza durumu signhub servisi tarafından entegrasyon servisine geri bildirilir.
 
### 2.8. İmzalama Sürecinin Tamamlanması
- Sürecin tamamlanması durumunda imzalanmış belge, FlowID ile beraber signhub servisinden indirilir.
 
---
 
## 3. Opsiyonel Adımlar
Bu süreçte, dökümanların gönderileceği ek süreçlere eklenmesi ve imzalanacak dökümanda belirli alanların seçilmesi (imza alanları, QR kod) gibi adımlar opsiyoneldir. İhtiyaç duyulması halinde süreç akışına dahil edilebilirler.
 
---
 
## 4. Süreç Akışının Görselleştirilmesi
Aşağıda adımları gösteren bir süreç diagramı bulunmaktadır:

![Onaylarım SignHub Sequence Diagram](https://raw.githubusercontent.com/DanialHuckabee/signhub.postman/main/Onaylar%C4%B1m%20SignHub%20Sequence%20Diagram.png "Sequence Diagram")