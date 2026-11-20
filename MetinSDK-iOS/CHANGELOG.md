# [v3.6.4] (2026-11-20 15:30:00)

File: MetinSDK.xcframework_v3.6.4.zip (iOS 15.0+, qurilma arm64 + simulyator arm64/x86_64)

Changes:
1. O'zMSt (O'z MSt 286:2024 (A) imzo, O'z MSt 285:2024 (A) hash) — yangi SDK 3.6.4, MKB KMS uchun.
2. Domen (host) cheklovi yo'q — istalgan KMS manzili (ichki IP ham) bilan ishlaydi.
3. addUser / getUser / addCertificate qaytarildi (O'zMSt): userPINFL, companyINN, dboUserId, passport, position majburiy.
4. Maydon qoidalari so'rovdan OLDIN tekshiriladi (InvalidArgumentException): PINFL — 14 raqam; INN — 9 yoki 14 raqam;
   dboUserId — musbat butun son; passport — 2 harf + 7 raqam (AA1234567 yoki PASUZ-AA1234567);
   phoneNumber — 998XXXXXXXXX; commonName / organisation / organisationUnit / position / locality / state — 64 belgigacha;
   address / email — 128 belgigacha.
5. getCertificate / sign / signCMS — serialNumber yoki 4 maydon (userPINFL + companyINN + dboUserId + passport) bo'yicha.
6. mobile_log — ilova initialize(...) da bergan Bearer token bilan yuboriladi (SDK ichida token yo'q).
7. Tekshirildi (MKB test KMS): addUser, getUser, addCertificate, getCertificate, sign, changePin, deleteCertificate (3 usul),
   clearCertificates, maxTryLimitPin (server cert-revoked), mobile_log. verify — server AS ulanishi tuzatilgach.
8. Barcha metodlar .userInitiated navbatida — birinchi sign/addCertificate sekinlashmaydi.



# [v1.1.7] (2026-04-05 12:12:43)

Changes:
1. generateOtp(), getUser(), addUser() - methodlar olib tashlandi, bu methodlar murojaat qiladigan endpointlar backend orqali kms-server bilan amalga oshiriladi.


# [v1.1.6] (2026-02-03 17:12:34)

Changes:
1. MetinManager.initialize(baseUrl: url, maxTryLimitPin: N) - sign qiliwda agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, .pinCodeMismatch(message, triesCount) xatolik qaytadi, agar limitga yetsa, .certificateRevoked qaytaradi.
2. addCertificate() qilinayotganda, berilayotgan userId o'sha userga tegishli ekanligiga tekshirildi va != bolsa .invalidArgument qaytariladi.
3. changePin() qilinayotganda ham, agar pin code ketma-ket maxTryLimitPin marta xato kiritilsa, cert revoke qilinadi va localdan o'chiriladi, har xato kiritilganda, .pinCodeMismatch(message, triesCount) xatolik qaytadi. Agar limitga yetsa, .certificateRevoked qaytaradi
4. deleteCertificate() va clearCertificates() methodlarida certificateni revoke qilish uchun request junatildi.
5. addCertificate(userId, dboUserId, ....) - dboUserId qoshildi, inn/pinfl birxil, faqat dboUserId orqali farqlash kerak bolganda, keyin getCertificate(dboUserId) methodda osha dboUserId orqali olib, uni serialNumberi orqali sign(serialNumber) methodda imzo qoyish mumkin boladi.
