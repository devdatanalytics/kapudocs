# Wataalamu wa Programu 

### Kutengeneza Programu ya KaPU Elimu
KaPU Elimu inajumuisha programu mbili za Retrieval-Augmented Generation (RAG), ambazo ni wasaidizi mnemba (chatbots) kwa Kiingereza na Kiswahili.
Kila moja ni chatbot inayosaidia wakulima kwa kujibu maswali yanayohusiana na magonjwa ya kuku katika lugha ya Kiingereza au Kiswahili. Chatbot ya KaPU Elimu inatumia vidokezo maalum, modeli kubwa za lugha (Large Language Model-LLM), na API kutoa majibu sahihi na yanayozingatia muktadha.

Program hizi mbili za RAG ya Kiingereza na RAG ya Kiswahili zinachanganya mbinu za akili mnemba (AI) za retrieval-based na generative kutoa majibu sahihi na yanayozingatia muktadha. Programu za RAG zinatumia kanzi data iliyofafanuliwa kuhusu magonjwa ya kuku na mbinu za usimamizi wa kilimo cha kuku kwa lugha ya Kiingereza na Kiswahili. Maswali maalum huhakikisha kuwa chatbots zinajibu tu maswali yanayohusiana na muktadha ulio kwenye kanzidata.

Vipengele Muhimu:

* Msaada wa lugha ya Kiingereza na Kiswahili kwa wakulima
* Inalenga maswali kuhusu magonjwa ya kuku na usimamizi wa mashamba ya kuku
* Uunganisho na API ya Sarufi kwa akili mnemba ya mazungumzo (Conversational AI)
* Maswali maalum kuhakikisha uhusiano na usahihi wa majibu


#### Hatua za Utengenezaji wa Program 
__1. Kukusanya na Kuchakata Taarifa__

Tulikusanya taarifa za kitaalamu kuhusu magonjwa ya kuku na mbinu za usimamizi wa mashamba ya kuku. Kisha, taarifa hizi zilihakikiwa na wataalam wa mifugo. Hatua iliyofuata ilikuwa kutengeneza kanzidata kwa kutumia hizi taarifa kwa lugha ya Kiingereza na Kiswahili. Baada ya hapo, tulichakata taarifa katika kanzidata kwa kutumia mbinu za uchunguzi wa maandishi (text extraction techniques) na kuzihifadhi katika kanzii data ya vekta kwa urahisi wa upatikanaji.

__2. Kuchagua Modeli kubwa ya Lugha (LLM)__

Programu ya KaPU Elimu ilitengenezwa kwa kutumia modeli kubwa ya lugha iitwayo `LLama3-70B-8192`. Modeli hii ni mfano wa modeli kubwa ya lugha yenye vigezo (parameters) bilioni 70 na eneo la muktadha lenye alama (tokens) 8192, vinavyohakikisha majibu bora kwa maswali yanayoulizwa na yanayozingatia muktadha. Mfano modeli ya `LLama3` ina uwezo wa kushughulikia maswali magumu na kutoa majibu bora, yanayozingatia muktadha. Tumefafanua mfano wa `LLama3` kwa yafuatayo:

* Idadi ya alama (tokens): Hiki ni kikomo cha idadi ya alama (maneno, sehemu za maneno, au herufi kulingana na mfano wa lugha) zinazoweza kutumika katika kutoa jibu. Hapa, kikomo cha alama ni 512, maana yake modeli itatoa majibu hadi kikomo hiki.
  
* Hali ya joto (temperature): Hiki ni kipengele kinachodhibiti ubunifu wa majibu. Thamani ya juu inafanya majibu kuwa ya ubunifu zaidi, wakati thamani ni ya chini inafanya majibu kuwa ya kubashiri zaidi. Katika kazi hii ya KaPU Elimu, Hali ya joto = 1, maana yake modeli inaleta usawa kati ya ubunifu na ufanisi.


__3. Kufafanua Maswali Maalum__

Vidokezo maalum (custom prompts) vinahakikisha chatbot inazingatia madhumuni yake na wigo wake.

Kidokezo kilichotumika kwa lugha ya Kiingereza ni:

`“You are a farmer assistant using English language to answer the farmer questions based on the document provided about poultry diseases. You don't need to answer any question not related to the knowledge on the document provided."`

Kidokezo kwa lugha ya Kiswahili ni:

`"Wewe ni msaidizi wa mkulima ukitumia lugha ya Kiswahili kujibu maswali ya mkulima kulingana na hati iliyotolewa kuhusu magonjwa ya kuku. Huna haja ya kujibu maswali yasiyohusiana na yaliyomo kwenye hati iliyotolewa"`
 
Kidokezo hiki kinahakikisha:

* Chatbot inajibu tu maswali yanayohusiana na magonjwa ya kuku
* Majibu yanatolewa kwa lugha ya Kiingereza au Kiswahili
* Hoja zisizo na maana zinapuuzwa

__4. Utekelezaji wa Retrieval-Augmented Generation (RAG)__

a.	Uorodheshaji wa Hati: Taarifa za msingi ziliwekwa katika vidokezo (tokenized) na kuhifadhiwa kwenye injini ya utafutaji wa data kwa mfumo wa vekta.

b.	Uchakataji wa Maswali: Wakati mtumiaji anapotuma swali, swali linatambuliwa na kulinganisha na sehemu zinazohusiana za hati. 

c.	Uundaji wa Majibu: Taarifa zilizopatikana zinapita kwenye modeli kubwa ya lugha, LLM, ambayo inaunda jibu kwa Kiswahili au Kiingereza kulingana na vidokezo vilivyotolewa.

__5. Utekelezaji (Deployment)__

Programu mbili za RAG zimetekelezwa kwa kuunganisha kwa API na kutumia jukwaa la <a href=https://www.sarufi.io/ target="_blank">Sarufi</a>, linaloruhusu uunganisho rahisi kwenye programu za wavuti na simu. Mchakato wa utekelezaji ulijumuisha yafuatayo:
 a. Kuanzisha kiungo cha API kutoka kwa Jukwaa la Sarufi
 
 b. Kuweka usahihi wa uthibitishaji na vichwa
 
 c. Kuweka API kwenye programu lengwa (wavuti au simu)

### Kutengeneza Programu ya KaPU Chunguza 

Programu ya KaPU Chunguza ilitengenezwa kwa kutumia mfumo wa Object detection wa kugundua na kuainisha vitu vyote kwenye picha. Tulitumia mfumo wa YOLOv8 kufundisha picha za kinyesi cha kuku kutambua madaraja matano (5). Madaraja haya ni Kuhara Damu (Coccidiosis), Kideri (Newcastle disease), Homa ya Matumbo (Salmonella), kuku wenye afya na mengine. Lengo la KaPU Chunguza ni kusaidia usimamizi wa afya ya kuku kupitia utambuzi wa mapema wa magonjwa.


__1. Mbinu za kufundisha Modeli__ 

1.1. Modeli ya Usanifu

* Modeli: YOLOv8s (toleo dogo) kwa matumizi ya simu 
* Maelezo: Modeli hii ya Object detection baada ya kufundishwa hutambua vitu katika picha kwa hatua moja kuzingatia uwiano kati ya kasi na usahihi, unaofaa kwa matumizi.

1.2. Seti ya Data

* Madaraja: 5 (Kuhara Damu (Coccidiosis), Kideri (Newcastle disease), Homa ya Matumbo (Salmonella), kuku wenye afya na mengine)
* Mgawanyo wa Seti ya Data:
    * Data za Mafunzo: picha 5129
    * Data za Uthibitishaji: picha 1449
* Chanzo: imefafanuliwa katika `data.yaml`
  > * <a href="https://zenodo.org/records/4628934#.Y4duFLJBzvU" target="_blank">Seti ya Data ya Kujifunza kwa Mashine ya Uchunguzi wa Magonjwa ya Kuku</a>
  > * <a href="https://zenodo.org/records/5801834" target="_blank">Seti ya Data ya Kujifunza kwa Mashine ya Uchunguzi wa Magonjwa ya Kuku - iliyofafanuliwa kwa mfumo wa PCR </a>

1.3. Vigezo vya Mafunzo ya Modeli 

* Uzito wa awali: `yolov8s.pt`
* Epoki: 500 (ustahimilivu wa mapema: 50)
* Ukubwa wa kundi: 16
* Ukubwa wa picha: 800x800 pixels
* Kiboreshaji: SGD (lr=0.01, momentum=0.9)
* Ongezeko la Data: Mipangilio chaguomsingi (ongezeko=Hapana)
* Viwango vya Upotevu:
  > * Upotevu wa Sanduku: 7.5
  > * Upotevu wa Uainishaji: 0.5
  > * Upotezaji wa Kielelezo cha Usambazaji (DFL): 1.5

1.4. Mazingira ya Mafunzo

* Vifaa: NVIDIA A10G GPU (22,516 MiB)
* Programu:
  > * Ultralytics YOLOv8.0.196 o Python 3.11.4
  > * PyTorch 2.0.1+cu118
  > * CUDA 11.8

__2. Vigezo vya Tathmini na Matokeo__

2.1 Matriki ya Madaraja:
<figure>
    <img src ="/kapudocs/assets/cmatrix.png" alt="matrix" style="width:50%">
    <figcaption>Matriki ya Madaraja</figcaption>
</figure>
* Hali ya Ufanisi: kuhara damu (74%), afya (70%), kideri (79%), mengine (85%), homa ya matumbo (83%)
* Madaraja yaliyokosewa: Mandhari ya nyuma mara nyingi huchanganywa na madaraja ya kuhara damu (22%), afya (25%), na kideri (21%)

2.2 Picha za Usahihi wa Utabiri na Uhalisia
<figure>
    <img src ="/kapudocs/assets/curve.png" alt="curve" style="width:50%">
    <figcaption>Picha za Usahihi wa Utabiri na Uhalisia</figcaption>
</figure>
* Wastani wa Usahihi (AP) kwa kila Daraja:
  > * kuhara damu (cocci): 0.737
  > * afya (healthy): 0.693 
  > * kideri (ncd): 0.757
  > * mengine (other): 0.764
  > * homa ya matumbo (salmo): 0.781
* mAP@0.5: 0.746

2.3 Utabiri

<figure>
    <img src ="/kapudocs/assets/predict.png" alt="predict" style="width:50%">
    <figcaption>Mifano ya utabiri wa magonjwa ya kuku</figcaption>
</figure>
* Mifano ya utabiri inaonyesha kugundua sahihi kwa madaraja ya kuhara damu (cocci) na afya (healthy), na masanduku yanayozunguka yanayoonekana katika maeneo yenye msongamano mkubwa.
* Alama za Usahihi: Alama za juu zinawiana na usahihi wa madaraja; alama za chini (mfano, 0.3) inaashiria kutokuwa na uhakika wa daraja.