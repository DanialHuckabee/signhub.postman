# SignHub E-İmza Entegrasyon Süreci Dokümanı
 
## 1. Entegrasyon Süreç Tarafları
- **İmza Atacak Kişi**: E-imza işlemini gerçekleştiren son kullanıcı.
- **Entegrasyon Servisi**: Onaylarım SignHub servisleri ile iletişim kuran, müşteri/kurum'a ait servis.
- **Onaylarıım SignHub Servisi**: Onaylarım işkurallarını barındıran servis.
 
---
 
## 2. Süreç Adımları
 
### 2.1. İmza Atacak Kişi Tarafından Talep
- İmza atacak kişi tarafından e-imza işleminin yapılması talep edilir.
### 2.2. Süreç Başlatma (CreateFlow)
- Entegrasyon servisi, süreci SignHub servisine istek atarak başlatır ve oluşturulan sürece bir **FlowId** (Süreç Kimliği) atanır. SignHub servisi atanan FlowId bilgisini Entegrasyon servisine döner.
- SignHub servisi tarafından oluşturulan FlowId, entegrasyon servisi tarafından saklanır.
 
### 2.3. İmzalanacak Dokümanın Eklenmesi
- FlowId kullanılarak imzalanacak doküman entegrasyon servisi tarafından SignHub servisine gönderilir.
- Gönderilen dokümanın bilgileri ve PageId (Sayfa Kimliği) SignHub servisi tarafından entegrasyon servisine döner. Entegrasyon servisi opsiyonel adımları kullanacaksa PageId bilgisini saklar*.
 
### 2.4. Gönderilecek Sürece Ek Dokümanlar Ekleme (Opsiyonel)
- İsteğe bağlı olarak, FlowId ile ilişkilendirilen sürece ek dokümanlar eklenebilir.
- PageId ile beraber doküman üzerinde imzaların ve QR kodun bulunacağı alanlar belirlenir.
 
### 2.5. Sürecin Başlatılması
- Entegrasyon servisi saklanan FlowId'sini SignHub servisine süreci başlatması için gönderir
- SignHub servisi süreci başlatılır ve imza atacak kişiye imza için açılması gereken URL döner. Bu URL, imzalama işlemi için pop-up olarak kullanıcıya gösterilir.
 
### 2.6. İmzalama İşlemi
- Kullanıcı, açılan imzalama arayüzünde (Onaylarım Sign Portal) e-imza aracını kullanarak imzalama işlemini gerçekleştirir.
 
### 2.7. Süreç Durumunun Takibi
- Entegrasyon servisi, sürecin durumunu **FlowId** ile takip eder. Bu işlem, scheduled jobs ile belirli aralıklarla yapılır.
- Süreç durumu ve imza durumu SignHub servisi tarafından entegrasyon servisine geri bildirilir.
 
### 2.8. İmzalama Sürecinin Tamamlanması
- Sürecin tamamlanması durumunda imzalanmış belge, FlowId ile beraber SignHub servisinden indirilir.
 
---
 
## 3. Opsiyonel Adımlar
Bu süreçte, dokümanların gönderileceği ek süreçlere eklenmesi ve imzalanacak dokümanda belirli alanların seçilmesi (imza alanları, QR kod) gibi adımlar opsiyoneldir. İhtiyaç duyulması halinde süreç akışına dahil edilebilirler.
 
---
 
## 4. Süreç Akışının Görselleştirilmesi
Aşağıda adımları gösteren bir süreç diagramı bulunmaktadır:

![Onaylarım SignHub Sequence Diagram](https://raw.githubusercontent.com/DanialHuckabee/signhub.postman/main/Onaylar%C4%B1m%20SignHub%20Sequence%20Diagram.png "Sequence Diagram")