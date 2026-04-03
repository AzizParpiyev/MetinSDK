# [v0.3.3] (2026-02-03 17:12:34)

Changes:
1. MetinSdk.initialize(context,baseUrl,maxTryLimitPin) - sign qiliwda agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, PinCodeMismatchException xatolik qaytadi (with triesCount). Agar limitga yetsa, CertificateRevokedException qaytaradi.
2. addCertificate() qilinayotganda, berilayotgan userId o'sha userga tegishli ekanligiga tekshirildi va != bolsa InvalidArgumentException qaytariladi.
3. changePin() qilinayotganda ham, agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, PinCodeMismatchException xatolik qaytadi. Agar limitga yetsa, CertificateRevokedException qaytaradi.
4. deleteCertificate() va clearCertificates() methodlarida certificateni revoke qilish uchun request junatildi.
5. addCertificate(userId, dboUserId) - dboUserId qoshildi, inn/pinfl birxil, faqat dboUserId orqali farqlash kerak bolganda, keyin getCertificateByDboUserId() methodda osha dboUserId orqali olib, uni serialNumberi orqali sign(serialNumber) methodda imzo qoyish mumkin boladi.

