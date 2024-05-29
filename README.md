# House Pricing Prediction
<p align='justify'>Real Estate adalah industri yang mengacu pada properti atau aset yang berwujud, seperti tanah, bangunan, atau struktur lainnya yang terletak di atas atau di dalam tanah. Di sebuah bisnis, real estate dapat menjadi objek investasi atau sumber pendapatan, seperti sewa atau penjualan properti. Machine Learning dapat berperan penting di industri real estate sepert memprediksi harga properti berdasarkan faktor-faktor seperti lokasi, ukuran, fasilitas, dan kondisi properti. Hal ini dapat membantu agen real estate, investor, dan penjual untuk menentukan harga yang tepat untuk properti mereka.</p>

<h3>Tujuan</h3>
<p align='justify'>Model diharapkan memiliki akurasi yang baik dan sudah teruji. Dan dapat memberikan insight bisnis kepada user</p>

<h3>Pembahasan</h3>
<p align="justify">Terdiri dari <b>1460 Baris</b> dan <b>81 Kolom</b></p>
<br>
<img height="50%" width="auto" alt="Missing Value Comparison" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/55c8499d-e94a-4173-be95-a91903361016">
<p align="justify">kolom data yang memiliki missing value tertinggi <b>PoolQC, MiscFeature, Alley, Fence, FireplaceQU </b> sehingga kolom - kolom tersebut bisa dihilangkan</p>
<br>
<img height="50%" width="auto" alt="Distribusi Data LotFrontage, GarageYrBlt, MasVnrArea" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/f594d12f-8a3c-4c1f-be93-dffc77579ebd">
<p align="justify">Untuk LotFrontage dan MasVnrArea <b>terindikasi Skewness Positif </b> karena itu untuk penanganan missing value menggunakan <b>median, </b> sedangkan GarageYrBlt bisa dibilang <b>distribusi normal</b> jadi bisa menggunakan <b>mean. </b> Dan untuk kolom yang mempunyai tipe data kategori untuk penanganan missing value bisa menggunakan <b>modus </b></p>
<br>
<img height="50%" width="auto" alt="Korelasi data numerik" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/17c79375-e860-459f-9e61-4fb176927c38">
<p align="justify">Setelah data dipisahkan antara kolom numerik dan kolom kategori, maka akan dilakukan filter terhadap kolom data yang bertipe numerik yang mempunyai korelasi rendah. Sehingga akan didapatkan kolom - kolom yang mempunyai korelasi tinggi. Setelah mendapatkan kolom - kolom data yang mempunyai korelasi tinggi dilakukan kembali filter untuk mendapatkan kolom - kolom yang mempunyai korelasi terhadap <b>SalePrice. </b> Ternyata kolom <b>'GarageYrBlt', 'MasVnrArea', 'Fireplaces' </b> tidak mempunyai korelasi terhadap <b>SalePrice </b> sehingga bisa dihilangkan saja</p>
<br>
<img height="300" width="auto" alt="Filter data kategori" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/4b513142-e814-4d40-a457-5d848a58f85d">
<p align="justify">Untuk kolom data yang bertipe kategori pemfilteran dilakukan dengan menghitung banyaknya kategori dari suatu kolom, ini dilakukan agar data terhindari dari imbalance</p>
<br>
<img height="300" width="auto" alt="Filter jenis data" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/f9a12cc7-4181-4038-96d3-ffd9b195df2e">
<p align="justify">Setelah mendapatkan kolom - kolom yang terbaik untuk model, langkah selanjutnya adalah memisahkan jenis dari setiap data agar memudahkan dalam membuat pipeline</p>
<br>
<img height="300" width="auto" alt="Encoder" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/39585751-9bee-40ca-be3f-bf5694fb6bd2">
<p align="justify">Untuk jenis data <b> kategori ordinal menggukan encoder OrdinalEncoder, </b> Sedangkan untuk jenis data <b> kategori nominal menggukan encoder OneHotEncoder</b></p>
<br>
<img height="300" width="auto"" alt="Hasil LazzyRegressor" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/467a24d5-bc7c-4c56-b915-5eb5ffe268c9">
<p align="justify">Untuk memilih algoritma bisa menggunakan <b>LazyRegressor</b> untuk membandingkan banyak algoritma regresi. Pada kasus ini algoritma terbaik adalah GradientBoostingRegressor, karena memiliki nilai <b> R-Squared yang tinggi, RMSE yang rendah, dan waktu pelatihan yang wajar (1.46 detik) </b>. Oleh karena itu, model ini bisa menjadi pilihan yang baik.</p>
<br>
<img height="200" width="auto" alt="Pipeline" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/8052d830-1ddc-4f4a-b2bd-ea907b9924b9">
<p align="justify">Setelah mendapatkan algoritma yang terbaik masukan kedalam pipeline. Dan lakukan hypertunning parameter untuk mendapatkan parameter terbaik</p>
<br>
<img height="100" width="auto" alt="Best Parameter" src="https://github.com/AptaArkana/House_Pricing_Prediction_Ames/assets/79633073/3d30818d-9cba-441e-905b-3d99651e69fd">
<p align="justify">Setelah dilakukan hyper parameter tunning dengan <b>metode GridSearch </b> didapatkan parameter terbaik yaitu <b>learning_rate: 0.1, max_depth: 2, min_samples_leaf: 30, n_estimators': 250. </b> Dengan hasil evaluasi menggunakan RMSE sebesar <b> 0.148983.</b></p>


