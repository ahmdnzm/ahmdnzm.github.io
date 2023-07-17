---
title: Error bash locales
date: 2023-05-24 12:00:00 +0800
categories: [Linux]
tags: [linux, ubuntu, bash, locales]     # TAG names should always be lowercase
image:
  path: /assets/img/cli.jpg
---
# Error bash locales

error shown when login from terminal

```shell
-bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
```
Install locales package

```shell
sudo apt install locales
```
check installed locales.

```shell
locale -a
```

From here, we know en_US.UTF8 not installed

```shell
C
C.utf8
POSIX
```

To install the missing locales, we can generate locale using this command

```shell
sudo dpkg-reconfigure locales
```

Output

```shell
Configuring locales
-------------------

Locales are a framework to switch between multiple languages and allow users to use their language, country, characters, collation
order, etc.

Please choose which locales to generate. UTF-8 locales should be chosen by default, particularly for new installations. Other
character sets may be useful for backwards compatibility with older systems and software.

  1. All locales               127. el_GR ISO-8859-7               253. gl_ES.UTF-8 UTF-8          379. ps_AF UTF-8
  2. C.UTF-8 UTF-8             128. el_GR.UTF-8 UTF-8              254. gl_ES@euro ISO-8859-15     380. pt_BR ISO-8859-1
  3. aa_DJ ISO-8859-1          129. el_GR@euro ISO-8859-7          255. gu_IN UTF-8                381. pt_BR.UTF-8 UTF-8
  4. aa_DJ.UTF-8 UTF-8         130. en_AG UTF-8                    256. gv_GB ISO-8859-1           382. pt_PT ISO-8859-1
  5. aa_ER UTF-8               131. en_AU ISO-8859-1               257. gv_GB.UTF-8 UTF-8          383. pt_PT.UTF-8 UTF-8
  6. aa_ER@saaho UTF-8         132. en_AU.UTF-8 UTF-8              258. ha_NG UTF-8                384. pt_PT@euro ISO-8859-15
  7. aa_ET UTF-8               133. en_BW ISO-8859-1               259. hak_TW UTF-8               385. quz_PE UTF-8
  8. af_ZA ISO-8859-1          134. en_BW.UTF-8 UTF-8              260. he_IL ISO-8859-8           386. raj_IN UTF-8
  9. af_ZA.UTF-8 UTF-8         135. en_CA ISO-8859-1               261. he_IL.UTF-8 UTF-8          387. ro_RO ISO-8859-2
  10. agr_PE UTF-8             136. en_CA.UTF-8 UTF-8              262. hi_IN UTF-8                388. ro_RO.UTF-8 UTF-8
  11. ak_GH UTF-8              137. en_DK ISO-8859-1               263. hif_FJ UTF-8               389. ru_RU ISO-8859-5
  12. am_ET UTF-8              138. en_DK.ISO-8859-15 ISO-8859-15  264. hne_IN UTF-8               390. ru_RU.CP1251 CP1251
  13. an_ES ISO-8859-15        139. en_DK.UTF-8 UTF-8              265. hr_HR ISO-8859-2           391. ru_RU.KOI8-R KOI8-R
  14. an_ES.UTF-8 UTF-8        140. en_GB ISO-8859-1               266. hr_HR.UTF-8 UTF-8          392. ru_RU.UTF-8 UTF-8
  15. anp_IN UTF-8             141. en_GB.ISO-8859-15 ISO-8859-15  267. hsb_DE ISO-8859-2          393. ru_UA KOI8-U
  16. ar_AE ISO-8859-6         142. en_GB.UTF-8 UTF-8              268. hsb_DE.UTF-8 UTF-8         394. ru_UA.UTF-8 UTF-8
  17. ar_AE.UTF-8 UTF-8        143. en_HK ISO-8859-1               269. ht_HT UTF-8                395. rw_RW UTF-8
  18. ar_BH ISO-8859-6         144. en_HK.UTF-8 UTF-8              270. hu_HU ISO-8859-2           396. sa_IN UTF-8
  19. ar_BH.UTF-8 UTF-8        145. en_IE ISO-8859-1               271. hu_HU.UTF-8 UTF-8          397. sah_RU UTF-8
  20. ar_DZ ISO-8859-6         146. en_IE.UTF-8 UTF-8              272. hy_AM UTF-8                398. sat_IN UTF-8
  21. ar_DZ.UTF-8 UTF-8        147. en_IE@euro ISO-8859-15         273. hy_AM.ARMSCII-8 ARMSCII-8  399. sc_IT UTF-8
  22. ar_EG ISO-8859-6         148. en_IL UTF-8                    274. ia_FR UTF-8                400. sd_IN UTF-8
  23. ar_EG.UTF-8 UTF-8        149. en_IN UTF-8                    275. id_ID ISO-8859-1           401. sd_IN@devanagari UTF-8
  24. ar_IN UTF-8              150. en_NG UTF-8                    276. id_ID.UTF-8 UTF-8          402. sd_PK UTF-8
  25. ar_IQ ISO-8859-6         151. en_NZ ISO-8859-1               277. ig_NG UTF-8                403. se_NO UTF-8
  26. ar_IQ.UTF-8 UTF-8        152. en_NZ.UTF-8 UTF-8              278. ik_CA UTF-8                404. sgs_LT UTF-8
  27. ar_JO ISO-8859-6         153. en_PH ISO-8859-1               279. is_IS ISO-8859-1           405. shn_MM UTF-8
[More]
```

```shell
	28. ar_JO.UTF-8 UTF-8        154. en_PH.UTF-8 UTF-8              280. is_IS.UTF-8 UTF-8          406. shs_CA UTF-8
  29. ar_KW ISO-8859-6         155. en_SC.UTF-8 UTF-8              281. it_CH ISO-8859-1           407. si_LK UTF-8
  30. ar_KW.UTF-8 UTF-8        156. en_SG ISO-8859-1               282. it_CH.UTF-8 UTF-8          408. sid_ET UTF-8
  31. ar_LB ISO-8859-6         157. en_SG.UTF-8 UTF-8              283. it_IT ISO-8859-1           409. sk_SK ISO-8859-2
  32. ar_LB.UTF-8 UTF-8        158. en_US ISO-8859-1               284. it_IT.UTF-8 UTF-8          410. sk_SK.UTF-8 UTF-8
  33. ar_LY ISO-8859-6         159. en_US.ISO-8859-15 ISO-8859-15  285. it_IT@euro ISO-8859-15     411. sl_SI ISO-8859-2
  34. ar_LY.UTF-8 UTF-8        160. en_US.UTF-8 UTF-8              286. iu_CA UTF-8                412. sl_SI.UTF-8 UTF-8
  35. ar_MA ISO-8859-6         161. en_ZA ISO-8859-1               287. ja_JP.EUC-JP EUC-JP        413. sm_WS UTF-8
  36. ar_MA.UTF-8 UTF-8        162. en_ZA.UTF-8 UTF-8              288. ja_JP.UTF-8 UTF-8          414. so_DJ ISO-8859-1
  37. ar_OM ISO-8859-6         163. en_ZM UTF-8                    289. ka_GE GEORGIAN-PS          415. so_DJ.UTF-8 UTF-8
  38. ar_OM.UTF-8 UTF-8        164. en_ZW ISO-8859-1               290. ka_GE.UTF-8 UTF-8          416. so_ET UTF-8
  39. ar_QA ISO-8859-6         165. en_ZW.UTF-8 UTF-8              291. kab_DZ UTF-8               417. so_KE ISO-8859-1
  40. ar_QA.UTF-8 UTF-8        166. eo UTF-8                       292. kk_KZ PT154                418. so_KE.UTF-8 UTF-8
  41. ar_SA ISO-8859-6         167. eo_US.UTF-8 UTF-8              293. kk_KZ.RK1048 RK1048        419. so_SO ISO-8859-1
  42. ar_SA.UTF-8 UTF-8        168. es_AR ISO-8859-1               294. kk_KZ.UTF-8 UTF-8          420. so_SO.UTF-8 UTF-8
  43. ar_SD ISO-8859-6         169. es_AR.UTF-8 UTF-8              295. kl_GL ISO-8859-1           421. sq_AL ISO-8859-1
  44. ar_SD.UTF-8 UTF-8        170. es_BO ISO-8859-1               296. kl_GL.UTF-8 UTF-8          422. sq_AL.UTF-8 UTF-8
  45. ar_SS UTF-8              171. es_BO.UTF-8 UTF-8              297. km_KH UTF-8                423. sq_MK UTF-8
  46. ar_SY ISO-8859-6         172. es_CL ISO-8859-1               298. kn_IN UTF-8                424. sr_ME UTF-8
  47. ar_SY.UTF-8 UTF-8        173. es_CL.UTF-8 UTF-8              299. ko_KR.EUC-KR EUC-KR        425. sr_RS UTF-8
  48. ar_TN ISO-8859-6         174. es_CO ISO-8859-1               300. ko_KR.UTF-8 UTF-8          426. sr_RS@latin UTF-8
  49. ar_TN.UTF-8 UTF-8        175. es_CO.UTF-8 UTF-8              301. kok_IN UTF-8               427. ss_ZA UTF-8
  50. ar_YE ISO-8859-6         176. es_CR ISO-8859-1               302. ks_IN UTF-8                428. st_ZA ISO-8859-1
  51. ar_YE.UTF-8 UTF-8        177. es_CR.UTF-8 UTF-8              303. ks_IN@devanagari UTF-8     429. st_ZA.UTF-8 UTF-8
  52. as_IN UTF-8              178. es_CU UTF-8                    304. ku_TR ISO-8859-9           430. sv_FI ISO-8859-1
  53. ast_ES ISO-8859-15       179. es_DO ISO-8859-1               305. ku_TR.UTF-8 UTF-8          431. sv_FI.UTF-8 UTF-8
  54. ast_ES.UTF-8 UTF-8       180. es_DO.UTF-8 UTF-8              306. kw_GB ISO-8859-1           432. sv_FI@euro ISO-8859-15
  55. ayc_PE UTF-8             181. es_EC ISO-8859-1               307. kw_GB.UTF-8 UTF-8          433. sv_SE ISO-8859-1
  56. az_AZ UTF-8              182. es_EC.UTF-8 UTF-8              308. ky_KG UTF-8                434. sv_SE.ISO-8859-15 ISO-8859-15
  57. az_IR UTF-8              183. es_ES ISO-8859-1               309. lb_LU UTF-8                435. sv_SE.UTF-8 UTF-8
  58. be_BY CP1251             184. es_ES.UTF-8 UTF-8              310. lg_UG ISO-8859-10          436. sw_KE UTF-8
  59. be_BY.UTF-8 UTF-8        185. es_ES@euro ISO-8859-15         311. lg_UG.UTF-8 UTF-8          437. sw_TZ UTF-8
  60. be_BY@latin UTF-8        186. es_GT ISO-8859-1               312. li_BE UTF-8                438. szl_PL UTF-8
  61. bem_ZM UTF-8             187. es_GT.UTF-8 UTF-8              313. li_NL UTF-8                439. ta_IN UTF-8
  62. ber_DZ UTF-8             188. es_HN ISO-8859-1               314. lij_IT UTF-8               440. ta_LK UTF-8
  63. ber_MA UTF-8             189. es_HN.UTF-8 UTF-8              315. ln_CD UTF-8                441. tcy_IN.UTF-8 UTF-8
[More]
```

```shell
	64. bg_BG CP1251             190. es_MX ISO-8859-1               316. lo_LA UTF-8                442. te_IN UTF-8
  65. bg_BG.UTF-8 UTF-8        191. es_MX.UTF-8 UTF-8              317. lt_LT ISO-8859-13          443. tg_TJ KOI8-T
  66. bhb_IN.UTF-8 UTF-8       192. es_NI ISO-8859-1               318. lt_LT.UTF-8 UTF-8          444. tg_TJ.UTF-8 UTF-8
  67. bho_IN UTF-8             193. es_NI.UTF-8 UTF-8              319. lv_LV ISO-8859-13          445. th_TH TIS-620
  68. bho_NP UTF-8             194. es_PA ISO-8859-1               320. lv_LV.UTF-8 UTF-8          446. th_TH.UTF-8 UTF-8
  69. bi_VU UTF-8              195. es_PA.UTF-8 UTF-8              321. lzh_TW UTF-8               447. the_NP UTF-8
  70. bn_BD UTF-8              196. es_PE ISO-8859-1               322. mag_IN UTF-8               448. ti_ER UTF-8
  71. bn_IN UTF-8              197. es_PE.UTF-8 UTF-8              323. mai_IN UTF-8               449. ti_ET UTF-8
  72. bo_CN UTF-8              198. es_PR ISO-8859-1               324. mai_NP UTF-8               450. tig_ER UTF-8
  73. bo_IN UTF-8              199. es_PR.UTF-8 UTF-8              325. mfe_MU UTF-8               451. tk_TM UTF-8
  74. br_FR ISO-8859-1         200. es_PY ISO-8859-1               326. mg_MG ISO-8859-15          452. tl_PH ISO-8859-1
  75. br_FR.UTF-8 UTF-8        201. es_PY.UTF-8 UTF-8              327. mg_MG.UTF-8 UTF-8          453. tl_PH.UTF-8 UTF-8
  76. br_FR@euro ISO-8859-15   202. es_SV ISO-8859-1               328. mhr_RU UTF-8               454. tn_ZA UTF-8
  77. brx_IN UTF-8             203. es_SV.UTF-8 UTF-8              329. mi_NZ ISO-8859-13          455. to_TO UTF-8
  78. bs_BA ISO-8859-2         204. es_US ISO-8859-1               330. mi_NZ.UTF-8 UTF-8          456. tpi_PG UTF-8
  79. bs_BA.UTF-8 UTF-8        205. es_US.UTF-8 UTF-8              331. miq_NI UTF-8               457. tr_CY ISO-8859-9
  80. byn_ER UTF-8             206. es_UY ISO-8859-1               332. mjw_IN UTF-8               458. tr_CY.UTF-8 UTF-8
  81. ca_AD ISO-8859-15        207. es_UY.UTF-8 UTF-8              333. mk_MK ISO-8859-5           459. tr_TR ISO-8859-9
  82. ca_AD.UTF-8 UTF-8        208. es_VE ISO-8859-1               334. mk_MK.UTF-8 UTF-8          460. tr_TR.UTF-8 UTF-8
  83. ca_ES ISO-8859-1         209. es_VE.UTF-8 UTF-8              335. ml_IN UTF-8                461. ts_ZA UTF-8
  84. ca_ES.UTF-8 UTF-8        210. et_EE ISO-8859-1               336. mn_MN UTF-8                462. tt_RU UTF-8
  85. ca_ES@euro ISO-8859-15   211. et_EE.ISO-8859-15 ISO-8859-15  337. mni_IN UTF-8               463. tt_RU@iqtelif UTF-8
  86. ca_ES@valencia UTF-8     212. et_EE.UTF-8 UTF-8              338. mnw_MM UTF-8               464. ug_CN UTF-8
  87. ca_FR ISO-8859-15        213. eu_ES ISO-8859-1               339. mr_IN UTF-8                465. ug_CN@latin UTF-8
  88. ca_FR.UTF-8 UTF-8        214. eu_ES.UTF-8 UTF-8              340. ms_MY ISO-8859-1           466. uk_UA KOI8-U
  89. ca_IT ISO-8859-15        215. eu_ES@euro ISO-8859-15         341. ms_MY.UTF-8 UTF-8          467. uk_UA.UTF-8 UTF-8
  90. ca_IT.UTF-8 UTF-8        216. eu_FR ISO-8859-1               342. mt_MT ISO-8859-3           468. unm_US UTF-8
  91. ce_RU UTF-8              217. eu_FR.UTF-8 UTF-8              343. mt_MT.UTF-8 UTF-8          469. ur_IN UTF-8
  92. chr_US UTF-8             218. eu_FR@euro ISO-8859-15         344. my_MM UTF-8                470. ur_PK UTF-8
  93. ckb_IQ UTF-8             219. fa_IR UTF-8                    345. nan_TW UTF-8               471. uz_UZ ISO-8859-1
  94. cmn_TW UTF-8             220. ff_SN UTF-8                    346. nan_TW@latin UTF-8         472. uz_UZ.UTF-8 UTF-8
  95. crh_UA UTF-8             221. fi_FI ISO-8859-1               347. nb_NO ISO-8859-1           473. uz_UZ@cyrillic UTF-8
  96. cs_CZ ISO-8859-2         222. fi_FI.UTF-8 UTF-8              348. nb_NO.UTF-8 UTF-8          474. ve_ZA UTF-8
  97. cs_CZ.UTF-8 UTF-8        223. fi_FI@euro ISO-8859-15         349. nds_DE UTF-8               475. vi_VN UTF-8
  98. csb_PL UTF-8             224. fil_PH UTF-8                   350. nds_NL UTF-8               476. wa_BE ISO-8859-1
  99. cv_RU UTF-8              225. fo_FO ISO-8859-1               351. ne_NP UTF-8                477. wa_BE.UTF-8 UTF-8
[More]
```

```shell
  100. cy_GB ISO-8859-14       226. fo_FO.UTF-8 UTF-8              352. nhn_MX UTF-8               478. wa_BE@euro ISO-8859-15
  101. cy_GB.UTF-8 UTF-8       227. fr_BE ISO-8859-1               353. niu_NU UTF-8               479. wae_CH UTF-8
  102. da_DK ISO-8859-1        228. fr_BE.UTF-8 UTF-8              354. niu_NZ UTF-8               480. wal_ET UTF-8
  103. da_DK.UTF-8 UTF-8       229. fr_BE@euro ISO-8859-15         355. nl_AW UTF-8                481. wo_SN UTF-8
  104. de_AT ISO-8859-1        230. fr_CA ISO-8859-1               356. nl_BE ISO-8859-1           482. xh_ZA ISO-8859-1
  105. de_AT.UTF-8 UTF-8       231. fr_CA.UTF-8 UTF-8              357. nl_BE.UTF-8 UTF-8          483. xh_ZA.UTF-8 UTF-8
  106. de_AT@euro ISO-8859-15  232. fr_CH ISO-8859-1               358. nl_BE@euro ISO-8859-15     484. yi_US CP1255
  107. de_BE ISO-8859-1        233. fr_CH.UTF-8 UTF-8              359. nl_NL ISO-8859-1           485. yi_US.UTF-8 UTF-8
  108. de_BE.UTF-8 UTF-8       234. fr_FR ISO-8859-1               360. nl_NL.UTF-8 UTF-8          486. yo_NG UTF-8
  109. de_BE@euro ISO-8859-15  235. fr_FR.UTF-8 UTF-8              361. nl_NL@euro ISO-8859-15     487. yue_HK UTF-8
  110. de_CH ISO-8859-1        236. fr_FR@euro ISO-8859-15         362. nn_NO ISO-8859-1           488. yuw_PG UTF-8
  111. de_CH.UTF-8 UTF-8       237. fr_LU ISO-8859-1               363. nn_NO.UTF-8 UTF-8          489. zh_CN GB2312
  112. de_DE ISO-8859-1        238. fr_LU.UTF-8 UTF-8              364. nr_ZA UTF-8                490. zh_CN.GB18030 GB18030
  113. de_DE.UTF-8 UTF-8       239. fr_LU@euro ISO-8859-15         365. nso_ZA UTF-8               491. zh_CN.GBK GBK
  114. de_DE@euro ISO-8859-15  240. fur_IT UTF-8                   366. oc_FR ISO-8859-1           492. zh_CN.UTF-8 UTF-8
  115. de_IT ISO-8859-1        241. fy_DE UTF-8                    367. oc_FR.UTF-8 UTF-8          493. zh_HK BIG5-HKSCS
  116. de_IT.UTF-8 UTF-8       242. fy_NL UTF-8                    368. om_ET UTF-8                494. zh_HK.UTF-8 UTF-8
  117. de_LI.UTF-8 UTF-8       243. ga_IE ISO-8859-1               369. om_KE ISO-8859-1           495. zh_SG GB2312
  118. de_LU ISO-8859-1        244. ga_IE.UTF-8 UTF-8              370. om_KE.UTF-8 UTF-8          496. zh_SG.GBK GBK
  119. de_LU.UTF-8 UTF-8       245. ga_IE@euro ISO-8859-15         371. or_IN UTF-8                497. zh_SG.UTF-8 UTF-8
  120. de_LU@euro ISO-8859-15  246. gd_GB ISO-8859-15              372. os_RU UTF-8                498. zh_TW BIG5
  121. doi_IN UTF-8            247. gd_GB.UTF-8 UTF-8              373. pa_IN UTF-8                499. zh_TW.EUC-TW EUC-TW
  122. dsb_DE UTF-8            248. gez_ER UTF-8                   374. pa_PK UTF-8                500. zh_TW.UTF-8 UTF-8
  123. dv_MV UTF-8             249. gez_ER@abegede UTF-8           375. pap_AW UTF-8               501. zu_ZA ISO-8859-1
  124. dz_BT UTF-8             250. gez_ET UTF-8                   376. pap_CW UTF-8               502. zu_ZA.UTF-8 UTF-8
  125. el_CY ISO-8859-7        251. gez_ET@abegede UTF-8           377. pl_PL ISO-8859-2
  126. el_CY.UTF-8 UTF-8       252. gl_ES ISO-8859-1               378. pl_PL.UTF-8 UTF-8

(Enter the items or ranges you want to select, separated by spaces.)

Locales to be generated: 160
```

Enter number 160 for en_US.UTF-8 UTF-8 

```shell
Many packages in Debian use locales to display text in the correct language for the user. You can choose a default locale for the
system from the generated locales.

This will select the default language for the entire system. If this system is a multi-user system where not all users are able to
speak the default language, they will experience difficulties.

  1. None  2. C.UTF-8  3. en_US.UTF-8
Default locale for the system environment: 3
```

Enter number 3 for en_US.UTF-8

Output


```shell
Generating locales (this might take a while)...
  en_US.UTF-8... done
Generation complete.
```

Exit terminal and login back to confirm the error is gone