<h1 align="center" style="color:#94C973">~ Detaylı 'Git' Rehberi ~</h1>

<h3 style="color:#B1D8B7"> Git Nedir </h3>

**'Git'** ücretsiz ve açık kaynak olarak tasarlanmış, proje büyüklüğü farketmeksizin, çoğu geliştiricinin tercih ettiği dağınık versiyon kontrol sistemi olarak tanımlanabilir. Versiyon kontrolü, üzerinde çalıştığımız projede ya da herhangi basit bir dosyada  zaman içerisinde gerçekleştirdiğimiz değişiklikleri kaydeden ve ihtiyaç duyduğumuzda bu değişiklikleri görüntüleyebilmemizi ve inceleyebilmemizi sağlayan sisteme verilen isim olarak düşünülebilir. Versiyon kontrol sistemi, bilgisiyarımızda üzerinde çalıştığımız ve değişiklikleri kayıt altına almak istediğimiz tüm dosyalara uygulanabilir. Bu bağlamda versiyon kontrol sistemi, yalnızca yazılım geliştiricilere değil akademisyeninden grafik tasarımcısına, mühendisinden yazarına kadar farklı meslek gruplarından herkese kolaylık sağlayan süper bir kaynak kontrol aracı. 

**'Git',** versiyon kontrolü (version control) veya başka bir deyişle kaynak yönetimi (source control) yapabildiğimiz tek yazılım aracı değil tabii ki. Büyük teknoloji firmalarının geliştiriciler için çıkardıkları kendi ürünlerinde de farklı versiyon takip sistemleri bulunuyor. Microsoft'un kendi geliştirme ortamı için çıkardığı Azure DevOps Server, Amazon'un AWS CodeCommit ve IBM'in Rational ClearCase yazılım araçları bunlara örnek olarak gösterilebilir. Şu an geliştiricilerin kullanımına açık tüm versiyon takip sistemlerine ve bunların karşılaştırmasına detaylı bir şekilde göz atmak istiyorsanuz [bu kaynak](https://www.g2.com/categories/version-control-systems) sizin için faydalı olabilir. 

Peki versiyon kontrolüne yönelik ihtiyaçlarımızı karşılayabilecek ve birbirinden farklı özelliklere sahip bunca yazılım aracı mevcutken, **Git'i** diğerlerinden ayıran özellikler neler? Neden versiyon takip sistemi denilince aklımıza direkt **Git** geliyor? Yazının başında da belirttiğim gibi **Git** açık kaynak ve kullanımı ücretsiz olan bir yazılım. Bu durum, tabii ki belirli bir ölçekte, dünyada özgür yazılım olarak geliştirilen çoğu projenin neden **Git'i** tercih ettiği konusunda fikir veriyor olabilir. Ancak CVS, Bazaar, Mercurial ve SVN gibi versiyon kontrol sistemleri de ücretsiz ve açık kaynak olarak kullanıma açık olmalarına rağmen nasıl oluyor da versiyon takip sistemi denilince insanların aklına ilk olarak **Git** geliyor?

**Git** öncelikle kullanıcılara süper hızlı ve kolay uygulanabilir bir deneyim sunuyor. Hızının ve kolay öğrenme sürecinin yanı sıra farklı işletim sistemlerinde de kullanılabiliyor oluşu **Git'e** büyük bir avantaj sağlıyor diyebiliriz. Ayrıca, **Git** bize yerel ortamımızda herhangi bir internet bağlantısına gerek olmadan projemizdeki işlem geçmişimizi inceleyebilme imkanı veriyor. Çevrimdışı özelliği yerel ortamımızda kullandığımız **Git'in** kıymetini daha da arttırıyor. Ancak özgür yazılım olarak piyasada kullanılan diğer versiyon kontrol sistemlerine nazaran **Git'in** sağladığı en büyük avantajlar 'local branching' (yerel ortamımızda projemizi geliştirme parçalarına ayırmak), 'convenient staging areas' (projemizdeki değişiklikleri kullanışlı ve hızlı bir şekilde sahneye almak) ve 'çoklu iş akışı imkanı' olarak belirtilebilir. Lafı daha da uzatmadan ve **Git'in** bu imkanları bize nasıl sağladığına yönelik teknik detaylara boğulmadan gelin bu müthiş aracı nasıl kullanacağımızı konuşalım. 

<h3 style="color:#B1D8B7"> Yerel Ortamda Git Kurulumu </h3>

Üzerinde çalıştığımız projelerimize **Git** versiyon takibi uygulamadan önce kullandığımız işletim sistemimizde **Git'in** yüklü olup olmadığını kontrol etmemiz gerekiyor. Terminal üzerinden aşağıda yazan komutu girerek, işletim sisteminizde git yüklü olup olmadığını kontrol edebilirsiniz. 

    $ git --version

Yazdığınız bu komut sonrasında aldığınız yanıt işletim sisteminizde yüklü olan **Git** versiyonunu size bildiriyorsa sıfırdan bir kurulum yapmanızı gerektirecek bir durum yok. Ancak bir hata mesajı veya **Git'in** yüklü olmadığına dair bir uyarı alıyorsanız makinenize sıfırdan kurulum yapmanız gerekiyor. Farklı işletim sistemleri için kurulumu aşağıda gösterildiği şekilde yapabilirsiniz. 

<h5 style="color:#2F5233"> Linux </h5>

Linux işletim sistemlerden RPM temelli olanlar için (Fedore, RHEL ya da CentOs):

    $ sudo dnf install git-all

Debian temelli olanlar için: (Ubuntu vb.)

    $ sudo apt install git-all

<h5 style="color:#2F5233"> MacOs </h5>

MacOs sistemleri için diğer sistemlerde olduğu gibi farklı yükleme seçenekleri mevcut. Eğer Git'i bilgisiyarınızın terminalinden hızlı ve pratik bir şekilde yüklemek istiyorsanız Xcode aracını kullanabilirsiniz. Eğer bilgisiyarınızda Xcode yüklü ise ilk aşamayı geçebilirsiniz.

    $ xcode-select --install

    $ git --version

Bilgisiyarınızda Git'in versiyonunu gerçekleştiren son komut sonrasında eğer Git MacOs sisteminizde yüklü değilse bilgisayarınız otomatik olarak size Git'i yüklemek isteyip istemediğinizi soracaktır. Yükleme seçeneğini işaretleyerek MacOs sisteminizde Git kurulumunu gerçekleştirebilirsiniz.

Xcode'dan farklı olarak Git versiyon takip sistemini işletim sisteminizde 'Homebrew' paket yönetim aracı aracılığıyla da kurabilirsiniz. Eğer MacOs sisteminizde 'Homebrew' yüklü ise ilk aşamayı geçebilirsiniz.

    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

    $ brew install git

    $ git --version

<h5 style="color:#2F5233"> Windows </h5>

Windows işletim sistemli bilgisiyarınıza Git kurulumu yapmak için bu [linkten](https://git-scm.com/download/win) yükleme paketini indirebilirsiniz. İndirmeyi tamamladıktan sonra kurulum paketini çalıştırarak aşamaları tamamlayıp, kurulumu gerçekleştirebilirsiniz. Windows işletim sistemi için detaylı kurulum rehberi olarak bu [sayfayı](https://phoenixnap.com/kb/how-to-install-git-windows) ziyaret edebilir ve takıldığınız noktalar olursa buradan destek alabilirsiniz. 

<h3 style="color:#B1D8B7"> Kurulumdan Sonra Temel Ayarlar </h3>

Git kurulumunu bilgisiyarınızda yaptıktan sonra, Git'in varsayılan olarak git/config dosyasında bulunan ayarları görüntülemek için aşağıdaki komutu yazabilirsiniz:

    $ git config --list --show-origin

Gelen yanıt sonrası, değiştirmek istediğiniz varsayılan ayarları kendinizce belirleyerek değişiklikleri yine komut satırından gerçekleştirebilirsiniz. Ancak öncelikle gerçekleştirmemiz gereken önemli bir adım var. Git'e kendi bilgilerimizi okutarak, versiyon takibinde kullanmasını sağlamalıyız. Bunun için de ismimizi ve e-posta adresimizi Git'in ayarlarında okumasını sağlayacağız. Bunun için: 

    $ git config --global user.name "Furkan Meraloğlu"
    $ git config --global user.email furkanmeraloglu@gmail.com

İsmimizi ve e-posta adresimizi Git config dosyasına kaydettikten sonra son olarak varsayılan 'branch' ismi olan 'master' ismini de istediğimiz bir şekilde değiştirebiliriz. Normalde yerel ortamımızda 'master' ismi ile sorunsuz çalışabiliyoruz ancak ilerleyen bölümlerde yerel depomuzu bir uzak depo olan GitHub'a bağlarken GitHub branch ismimizi 'main' olarak değiştirmemizi talep edecek. GitHub'ın neden böyle bir değişiklik istediğini merak edenler olursa bu [yazıyı](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main) okuyabilirler. Master Branch ismini Main yapmak için aşağıdaki komutu terminalimizde çalıştırıyoruz:

    $ git config --global init.defaultBranch main

Kurulum sonrası temel ayarlarımızı da yaptık. Eğer ayarlarda yaptığınız değişiklikleri görmek istiyorsanız aşağıdaki komutu kullanabilirsiniz. 

    $ git config --list

<h3 style="color:#B1D8B7"> Temel Giriş ve İlk Git Deposu </h3>

Git'i bilgisiyarınıza başarıyla kurdunuz, gerekli ya da tercihe bağlı tüm ayarlarınızı yaptınız. Artık üzerinde çalıştığınız dosyalarda versiyon takip sistemi başlatabilir, projelerinizin zaman içerisindeki gelişimini ve gerçekleşen değişiklikleri kolaylıkla takip edebilir, projeyi istediğiniz noktaya geri döndürebilir, başka bir proje ile birleştirebilir veya isterseniz uzak bir Git deposu kullanarak yaptıklarınızı başka insanlarla paylaşabilirsiniz. Bunların hepsini nasıl yapacağım ben diye endişelenmeyin, bu rehberi okuduktan sonra artık projelerinizde versiyon takip sistemi kullanmanın rahatlığını yaşayacaksınız.

<h5 style="color:#2F5233"> Windows </h5>



