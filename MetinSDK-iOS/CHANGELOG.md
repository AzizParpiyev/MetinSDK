# [v1.1.6] (2026-02-03 17:12:34)

Changes:
1. MetinManager.initialize(baseUrl: url, maxTryLimitPin: N) - sign qiliwda agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, .pinCodeMismatch(message, triesCount) xatolik qaytadi, agar limitga yetsa, .certificateRevoked qaytaradi.
2. addCertificate() qilinayotganda, berilayotgan userId o'sha userga tegishli ekanligiga tekshirildi va != bolsa .invalidArgument qaytariladi.
3. changePin() qilinayotganda ham, agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, .pinCodeMismatch(message, triesCount) xatolik qaytadi. Agar limitga yetsa, .certificateRevoked qaytaradi
4. deleteCertificate() va clearCertificates() methodlarida certificateni revoke qilish uchun request junatildi.
5. addCertificate(userId, dboUserId, ....) - dboUserId qoshildi, inn/pinfl birxil, faqat dboUserId orqali farqlash kerak bolganda, keyin getCertificate(dboUserId) methodda osha dboUserId orqali olib, uni serialNumberi orqali sign(serialNumber) methodda imzo qoyish mumkin boladi.