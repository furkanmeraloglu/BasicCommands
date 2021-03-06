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

İsmimizi ve e-posta adresimizi Git config dosyasına kaydettikten sonra son olarak varsayılan 'branch' ismi olan 'master' ismini de istediğimiz bir şekilde değiştirebiliriz. Normalde yerel ortamımızda 'master' ismi ile sorunsuz çalışabiliyoruz ancak ilerleyen bölümlerde yerel depomuzu bir uzak depo olan GitHub'a bağlarken GitHub branch ismimizi `main` olarak değiştirmemizi talep edecek. GitHub'ın neden böyle bir değişiklik istediğini merak edenler olursa bu [yazıyı](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main) okuyabilirler. `Master` Branch ismini `main` yapmak için aşağıdaki komutu terminalimizde çalıştırıyoruz:

    $ git config --global init.defaultBranch main

Kurulum sonrası temel ayarlarımızı da yaptık. Eğer ayarlarda yaptığınız değişiklikleri görmek istiyorsanız aşağıdaki komutu kullanabilirsiniz. 

    $ git config --list

<h3 style="color:#B1D8B7"> Git Kullanımı </h3>

Git'i bilgisiyarınıza başarıyla kurdunuz, gerekli ya da tercihe bağlı tüm ayarlarınızı yaptınız. Artık üzerinde çalıştığınız dosyalarda versiyon takip sistemi başlatabilir, projelerinizin zaman içerisindeki gelişimini ve gerçekleşen değişiklikleri kolaylıkla takip edebilir, projeyi istediğiniz noktaya geri döndürebilir, başka bir proje ile birleştirebilir veya isterseniz uzak bir Git deposu kullanarak yaptıklarınızı başka insanlarla paylaşabilirsiniz. Bunların hepsini nasıl yapacağım ben diye endişelenmeyin, bu rehberi okuduktan sonra artık projelerinizde versiyon takip sistemi kullanmanın rahatlığını yaşayacaksınız.

Terminali kullanarak versiyon takibine almak istediğimiz dosyanın dizinine gidiyoruz ve sonra aşağıdaki komut satırını çalıştırıyoruz: 

    $ git init

Bu komutla dosyanızda Git versiyon takibini başlattınız. Dosyanız içerisinde yaptığınız tüm değişiklikleri artık versiyon takip sistemi ile takip edebilir ve yukarıda bahsettiğimiz tüm işlemleri gerçekleştirebilirsiniz. Artık dosyanız içerisinde yeni bir belge oluşturduğunuz anda veya var olan belgelerinizde bir değişiklik yaptığınız anda tüm değişiklikler Git tarafından takip edilecek. Peki takibe aldığımız dosyamız içerisinde bir belge oluşturduk diyelim. Terminalimize döndüğümüzde takibini başlattığımız dosyanın durumunu sorguladığımızda değişiklik yapıldığına dair bir bilgilendirme yazısı ile karşılaşacağız. Versiyon durumunu sorgulamak için aşağıdaki komutu terminalinizde çalıştırabilirsiniz: 

    $ git status

Dosyanızda yaptığınız bu değişiklikleri kayıt altına almak istiyorsanız önce değişiklikleri sahneye almanız (stage) ve daha sonrasında işlemeniz (commit) gerekiyor. Sırasıyla aşağıdaki komutları terminalizde çalıştırarak değişikliklerinizi işleme alabilirsiniz: 

    $ git add {belge_adi}
    $ git commit -m {commit başlığı}

Yukarıdaki ilk komutta {belge_adi} olarak belirtilen bölüme sahneye almak istediğiniz belgenin adını giriyorsunuz. Ya da isterseniz dosyanızdaki tüm değişiklikleri sahneye almak için aşağıdaki komutu da girebilirsiniz: 

    $ git add -A

Değişiklikleri sahneye aldıktan sonra işlemek (commit) için yazdığımız komutta `-m` ifadesinden sonra bu değişiklikleri hangi başlık altında kayıt altına almak istediğinizi belirtebilirsiniz. Dosyamızda yaptığımız her değişiklik sonrası tüm değişiklikleri sahneye almayı unutmayın. Peki bir değişiklik yaptıktan sonra değişikliği sahneye alıp commit'lediniz. Ama sonrasında o dosya üzerinde yine bir değişiklik yapmak istiyorsunuz ancak bu değişikliğin farklı bir commit başlığı altında kaydedilmesini istemiyorsunuz. Bu durumda aşağıdaki komutu kullanarak bir önceki commit başlığı altında dosyanızın güncel halini commit'leyebilirsiniz.

    $ git add {belge_adi}
    $ git commit --amend

veya isterseniz son commitinizin ismini de değiştirerek öyle işleme alabilirsiniz.

    $ git commit --amend -m {commit başlığı}

Peki dosyanızda yapış olduğunuz bir değişikliği geri almak istiyorsunuz. Bu durumda aşağıdaki komutu kullanabilirsiniz.

    $ git checkout -- {belge_adi}

veya

    $ git restore {belge_adi}

Ya da değişiklik yaptıktan sonra sahneye aldığınız bir belgenizi sahneden çıkarmak istiyorsunuz (unstage). Bu durumda aşağıdaki komutu kullanabilirsiniz.

    $ git reset HEAD {belge_adi}

veya 

    $ git restore --staged {belge_adi}

Takip sistemi başlattığınız dosyanızdaki tüm commit geçmişinizi aşağıdaki komutu çalıştırarak görebilirsiniz.

    $ git log

Bu komutu çalıştırdıktan sonra terminal size dosyanızda yapmış olduğunuz commitleri hash'li ID Tag'leri ile birlikte gösterecek. Commitlerin sahip oldukları ID Tag'lerini kullanarak iki commit arasında ne değişiklikler yapıldığını dilediğiniz gibi görüntüleyebilirsiniz. Bunun için aşağıdaki komutu çalıştırmanız yeterli.

    $ git diff {IDTag1} {IDTag2}

İki commit arasındaki değişiklikleri görmenin yanı sıra commitlerin ID Tag'lerini kullanarak isterseniz dosyanızda dilediğiniz yere dönebilirsiniz. 

    $ git revert {IDTag}

veya 

    $ git reset --hard {IDTag}

Git ile yapabileceklerimiz sadece dosyamız üzerinde yaptığımız değişiklikleri takip etmekle sınırlı değil tabii ki. Diyelim ki bir proje üzerinde çalışıyoruz ve proje dosyamızda versiyon takip sistemi başlattık. Ancak biz yapacağımız tüm değişikliklerimizi ana branch'imiz olan `main` değil de `development` üzerinde sahneye almak ve commitlemek istiyoruz. Bunu ilk okuduğunuzda "neden böyle yapayım ya çok saçma" diyebilirsiniz. Büyük bir teknoloji şirketinin üzerinde geliştirmelerine devam ettiği bir yazılım projesi olduğunu düşünün. Peki sizce bu proje hayata geçirildikten sonra yapılacak olan değişikliklerin tek branch üzerinden mi gerçekleşmesi daha etkili bir yöntem olurdu yoksa projenin her versiyonu için farklı bir branch üzerinden mi gidilseydi daha etkili olurdu? İşte bu noktada 'branch' kavramının önemini bir kez daha gözümüzün önüne getirebiliriz. Lafı fazla uzatmadan üzerinde çalıştığımız projede nasıl yeni bir branch oluşturulacağını, oluşturulan branchler arasında nasıl seçim yapılacağını ve son olarak bu branchleri nasıl birleştireceğimizi gelin hep beraber görelim. 

Versiyon takip sistemi başlattığımız ve değişikliklerimizi commitlediğimiz dosyamızda yeni bir branch oluşturmak için aşağıdaki komutu çalıştırıyoruz.

    $ git branch {branch_adi}

Oluşturduğumuz branch'e geçmek istediğimizde aşağıdaki komutu çalıştırıyoruz.

    $ git checkout {branch_adi}

Bir branch oluşturup aynı komut içerisinde yeni oluşturduğunuz branch'e geçmek istiyorsanız aşağıdaki komutu çalıştırabilirsiniz.

    $ git checkout -b {branch_adi}

Peki sonradan oluşturduğumuz branch'in ismini nasıl değiştireceğiz? Aşağıdaki komutu çalıştırdığınız zaman branch isminiz değişecektir. 

    $ git branch --move {eski branch_adi} {yeni branch_adi}

`Main` branch'i haricinde oluşturduğunuz branch'te istediğiniz değişiklikleri yapabilirsiniz. Ancak bu branch'te yaptığınız değişiklikleri sahneye almadan ve commit'lemeden `main` branch'e geçemezsiniz. Değişikliklerinizi commit'ledikten sonra `main` branch'e geçip projenizin ana hattı üzerinde değişiklik yapabilir, hatta yaptığınız değişiklikleri başka bir branch'te depolayabilirsiniz. Bu esneklik size projeniz üzerinde tam hakimiyete sahip olmanızı sağlamakla beraber istediğiniz noktaya dönmenizi sağlar. 

Diyelim ki `main` branch'iniz dışında oluşturduğunuz branch'te yapmak istediğiniz değişiklikleri yaptınız ve bu branch'i `main` branch ile birleştirmek istiyorsunuz. Bunu yapmak için aşağıdaki komut satırlarını çalıştırabilirsiniz.

    $ git checkout main
    $ git merge {main ile birleştireceğiniz branch_adı}

Gördüğünüz gibi öncelikle `main` branch'e geçtik ve sonradan oluşturduğumuz branch'i `main`ile birleştirdik. Oluşturduğunuz branch'leri `main` ile birleştirdikten sonra isterseniz silebilirsiniz. Branch'i silmek için ise aşağıdaki komutu kullanabilirsiniz.

    $ git branch -d {branch_adi}

Peki merge işlemi yapmak istiyoruz ama birleştirmek istediğimiz branch `main` branch'imizin önünde yer alıyor. Bu durumda Git bize bir `conflict` uyarısı gösterecektir. Bu `conflict` uyarısı size ortaya çıkan çakışmayı çözdükten sonra `merge` etmenizi söyleyecek. Peki bu çakışma durumunu nasıl düzelteceğiz? Çakışma olan belgeyi incelediğimizde Git'in belge içinde çakışma olan kısmı `<<<<<<<`, `=======`, `>>>>>>>` işaretleri ile gösterdiğini fark edeceksiniz. Bu çakışmayı çözmeniz için çakışan kısımları düzeltmeniz ve sonrasında branch'lerinizi birleştirmeniz yeterli. Birleştirdiğiniz yani `merge` ettiğiniz branch'leri görüntülemek istiyorsanız; 

    $ git branch --merged

ya da `merge` edilmemiş branch'leri görüntülemek istiyorsanız aşağıdaki komutları çalıştırabilirsiniz.

    $ git branch --no-merged

Ayrıca, Git, dökümanlarında `merge` komutunun dışında aynı zamanda `rebase` komutunu da kullanılabileceğimizi belirtiyor. Bu bağlamda birleştirmek istediğimiz branch'leri `rebase` komutu kullanarak aşağıdaki gibi birleştirebiliriz.

    $ git rebase {birleştirilmek istenen branch_adı}

<h3 style="color:#B1D8B7"> GitHub Kullanımı </h3>

İşletim sisteminizde Git kurulumu yaptıktan sonra yukarıda yaptığımız tüm işlemleri yerel ortamınızda gerçekleştirebilir ve dosyalarınızda versiyon takip sistemini kullanabilirsiniz. Peki takım halinde bir proje üzerinde çalıştığımızı düşünelim ya da yerel ortamda ürettiğimiz projeyi açık kaynak olarak başkalarının kullanımına açmak istediğimizi düşünelim. GitHub sunucularında oluşturacağımız `remote repository` tüm bu isteklerimizi karşılayacak. Öncelikle bir GitHub profiline sahip olmanız gerekiyor. [Buraya](https://github.com/) tıklayarak ücretsiz bir şekilde kayıt olabilir, projelerinizi paylaşabilir, takım arkadaşlarınızla ortak çalıştığınız projeler üzerinde işbirliği yapabilir veya farklı meslek gruplarından ve ilgi alanlarından olan birçok kişinin projelerini inceleyebilirsiniz. 

GitHub'da profilinizi oluşturduktan sonra `repositories` kısmına gelerek yeni bir depo oluşturabilirsiniz. Oluşturacağınız bu deponun başkaları tarafından erişilebilir olup olmayacağına karar verebilir ve isterseniz projeniz için bir açıklama yazısı yani `Readme.md` yazabilirsiniz. GitHub'daki deponuzu oluşturduktan sonra eğer yerel ortamınızda halihazırda var olan bir Git deposunu buraya aktarmak istiyorsanız aşağıdaki komutları yerel ortamınızdaki proje dizininden çalıştırabilirsiniz.

    $ git remote add origin https://github.com/furkanmeraloglu/test.git
    $ git branch -M main
    $ git push -u origin main

Yerel ortamınızdan GitHub deponuza aktaracağınız projede eğer versiyon takip sistemi başlatmamışsanız aşağıdaki komutları çalıştırabilirsiniz.

    $ echo "# test" >> README.md
    $ git init
    $ git add README.md
    $ git commit -m "first commit"
    $ git remote add origin https://github.com/furkanmeraloglu/test.git
    $ git push -u origin main

Bu aşamalardan sonra yerel ortamınızda sahip olduğunuz projeniz GitHub deponuzda da saklanmaya başlayacak. Peki yerel ortamınızda kullandığınız versiyon takip sistemi ile GitHub'daki deponuz arasında nasıl bağlantı kuracağız? Yerel ortamdaki değişiklikleri nasıl GitHub'a da göndereceğiz? Aslında bu sorunun cevabu yukarıda gizli. Yerelde commit'lediğimiz her değişikliği, yerel deponun bağlı bulunduğu `remote repository`'e `git push` komutu ile yollayabiliyoruz.

Peki bir takım arkadaşımız ortak projemize katkıda bulunmamız için bizi kendi GitHub deposunda `collaborator` olarak tanımladı. Biz bu depodaki proje dosyalarını kendi yerel ortamımıza alıp versiyon takibini nasıl sağlayacağız? Aşağıdaki komutu çalıştırarak GitHub deposunda yer alan bir projeyi yerel ortamınıza kolayca çekebilirsiniz.

    $ git clone git@github.com:furkanmeraloglu/test.git

Projeyi yerel ortamınıza aldıktan sonra bu rehberde ihtiyaçlarınızı karşılayacak tüm işlemleri gerçekleştirebilirsiniz.

<h3 style="color:#B1D8B7"> Sonuç </h3>

Evet, kapsamlı bir rehberin sonuna geldik. Bu rehber yardımıyla, versiyon takip sisteminin ne olduğu, neden böyle bir sisteme ihtiyacımız olduğu, ve bu sistemler arasında en yaygın biçimde kullanılan Git ve GitHub'ın nasıl kullanılacağı hakkında bilgi sahibi olmuş olduk. Temel fonksiyonlarına değindiğimiz Git hakkında daha detaylı bir dökümana ihtiyacınız var ise bu [bağlantıdan](https://git-scm.com/book/en/v2) Git'in detaylı rehber kitabına ulaşabilirsiniz. 