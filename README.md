# 🎬 Polars ilə Film Reytinqlərinin və İstifadəçi Davranışlarının Təhlili

Bu layihə **Polars** kitabxanasından istifadə edərək genişmiqyaslı film reytinqləri datasetinin təmizlənməsi, transformasiyası və biznes yönümlü təhlilini (EDA) əhatə edir. Layihədə yüksək performanslı dat çərçivələri (DataFrames) vasitəsilə istifadəçi davranışları, film populyarlığı və janr fəallıqları analiz olunmuşdur.

---

## 🛠️ İstifadə Olunan Texnologiyalar və Kitabxanalar
* **Dil:** Python 3.x
* **Data Processing:** Polars
* **Mühit:** Google Colab / Jupyter Notebook
* **Dataset:** MovieLens (Movies, Ratings, Tags)

---

## 📁 Dataset haqqında Məlumat

Proyekt 3 əsas relasiyalı cədvəl üzərində qurulmuşdur:

1. **`movies.csv`**: Filmlərin unikal ID-si (`movieid`), adı (`title`) və janrları (`genres`).
2. **`ratings.csv`**: İstifadəçilərin (`userid`) filmlərə verdiyi 0.5–5.0 aralığındakı qiymətləndirmələr (`rating`) və zaman damğası (`timestamp`).
3. **`tags.csv`**: İstifadəçilərin filmlərə təyin etdiyi xüsusi açar sözlər (`tag`) və yaradılma vaxtı (`tag_timestamp`).

---

## 🧹 Məlumatın Təmizlənməsi və Hazırlanması (Data Cleaning & Preprocessing)

Polars-ın verdiyi üstünlüklərdən istifadə edərək aşağıdakı təmizləmə və transformasiya addımları yerinə yetirilmişdir:
* **Sütun Adlarının Standartlaşdırılması:** Bütün cədvəllərdəki sütun adları kiçik hərflərə çevrilmişdir (`to_lowercase()`).
* **Sütunların Yenidən Adlandırılması:** `tags` cədvəlindəki `timestamp` sütunu `ratings` cədvəli ilə toqquşmaması üçün `tag_timestamp` olaraq yenidən adlandırılmışdır.
* **Məlumat Bütövlüyü Yoxlanışı:** Null (boş), NaN və təkrarlanan (duplicate) sətirlərin mövcudluğu yoxlanılmışdır.
* **Məntiqi Dublikatların Filterlənməsi:** Bir istifadəçinin eyni filmə birdən çox reytinq verməsi ssenarisi yoxlanılmış və datanın təmizliyi təmin edilmişdir.

---

## 📊 Ölçülən Əsas KPI-lar (Key Performance Indicators)

Proyekt çərçivəsində platforma performansını və istifadəçi fəallığını qiymətləndirmək üçün aşağıdakı əsas göstəricilər hesablanmışdır:

* **Orta Reytinq Balı (Average Rating):** Filmlərin və janrların ümumi məmnuniyyət səviyyəsi.
* **Qiymətləndirmə Sıxlığı / Həcmi (Rating Count/Volume):** Hər bir film üzrə toplanan ümumi səs sayı (populyarlıq göstəricisi).
* **Yüksək Reytinq Nisbəti (High Rating Proportion - HRP):** Filmin aldığı ümumi səslər içərisində 4.0 və üstü reytinqlərin faiz payı.
* **İstifadəçi Fəallığı İndeksi (User Engagement Level):** Hər bir istifadəçinin verdiyi reytinq və əlavə etdiyi teq (tag) sayı.
* **Janr Prioriteti və Həcmi:** Müəyyən janrların kütləvi izlənmə və bəyənilmə nisbəti.

---

## 📈 Əsas Analiz Nəticələri (Key Findings)

Polars vasitəsilə aparılan data analizi nəticəsində aşağıdakı mühüm məqamlar aşkar edilmişdir:

1. **Reytinq Sayı və Bəyənmə Korrelyasiyası:** Ən yüksək orta bala (5.0) sahib olan filmlərin böyük əksəriyyəti cəmi 1 və ya 2 istifadəçi tərəfindən qiymətləndirilib. Çox səs toplayan (populyar) filmlərdə isə orta bal 3.8 – 4.3 aralığında stabilləşir.
2. **Dominant Janrlar:** *Drama*, *Comedy* və *Action* janrları həm ümumi baxış sayına, həm də istifadəçi fəallığına görə ilk sıralardadır. 
3. **Yüksək Performanslı Xüsusi Janrlar:** *Film-Noir*, *War* və *Documentary* kimi spesifik janrlar daha az səs toplasa da, Yüksək Reytinq Nisbətinə (HRP) görə ən yüksək məmnuniyyət faizinə sahibdir.
4. **Teq (Tag) İstifadəsi və İstifadəçi Nişanlılığı:** İstifadəçilərin yalnız kiçik bir hissəsi (fəal istifadəçilər) teq əlavə edir. Ən çox istifadə olunan teqlər filmin əhval-ruhiyyəsi (mood), rejissoru və ya spesifik süjet xətti (*e.g., 'classic', 'sci-fi', 'atmospheric'*) ilə bağlıdır.

---

## 💡 Strateji Tövsiyələr və Biznes Təklifləri (Recommendations)

Aşkar olunmuş nəticələrə əsasən film platforması / tövsiyə sistemi üçün aşağıdakı addımlar məqsədəuyğundur:

* **Tövsiyə Mühərrikinin Optimization olunması (Bayesian Average Filtering):** Yalnız 1 səs alaraq 5.0 olan filmlərin tövsiyə sistemində ilk sıraya çıxmaması üçün reytinq hesablamasında *Bayesian Average* algoritmindən istifadə edilməlidir (səs sayının çəkisi nəzərə alınmalıdır).
* **Kolleksiya və Seqmentasiya (Niche Targeting):** *Film-Noir* və *Documentary* kimi yüksək məmnuniyyət faizi olan, lakin az tanınan janrlar üçün xüsusi "Mütəxəssis Seçimi" və ya "Gizli Şahəsərlər" kateqoriyaları yaradılmalıdır.
* **İstifadəçi Aktivliyinin Həvəsləndirilməsi (Gamification):** Teq yazan və dərin rəy bildirən istifadəçilər üçün nişanlar (badges) və ya loyallıq xalları tətbiq edilərək platformadakı orqanik kontent (metadata) zənginləşdirilməlidir.
* **Korrelyasiyaya Əsaslanan Personalizasiya:** İstifadəçinin bəyəndiyi teqlər və yüksək reytinq verdiyi spesifik janr kombinasiyaları (*e.g., 'Action|Sci-Fi'*) əsasında fərdiləşdirilmiş bildirişlər və tövsiyə siyahıları hazırlanmalıdır.
