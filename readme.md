# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default {
  // other rules...
  parserOptions: {
    ecmaVersion: "latest",
    sourceType: "module",
    project: ["./tsconfig.json", "./tsconfig.node.json"],
    tsconfigRootDir: __dirname,
  },
};
```

- Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
- Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list

proje adimlari :

1- npm install -g pnpm
2- pnpm create vite
3- porje adini . ile belirliyorum
4- react i ve ardindan typescript seciyorum
5- pnpm install
6- pnpm dev
7- mui yukleyecegiz
pnpm add @mui/material @emotion/react @emotion/styled
pnpm add @mui/icons-material

8- pages klasoru aciyorum icine home.tsx

9- components klasoru icini addtodocomp ve todolist.tsx ve todolistitem.tsx componentlerini olusturuyorum

10- pnpm add axios

11- app.tsx icine container aciyor icine home u yaziyorum tabiki importlari yapiyorum

12- home icine containe aciyorum icine typography atiyorum.importlari unutma.bunun icine todoapp with typescript basligini atarim. Altina addtodocomp ve todolist componentlerini cagiririm

13- home icinde todos stateini olustururum.yine usestati importunu unutma.bu zamana kadar reacttan farki yok

14- gettodos fonk olustur. try catch yapisi icinde axios kullan ve veriyi cek.Tabi bu ts oldugu icin benden type bekler.ben apime gore type belirleyecegim . api den gelen bilgiler object lerden olustugu icin type tanimlamasi interface olacak.Bu yuzden interface icinde id : string | number isdone : boolean task : string todo: string olacak.apide todo yok normalde . o yuzden onu optional yapicam yani ? isareti ile yapicam.Interface su anda hazir.

15- simdi interface i kullanmam lazim. use state icine <[] as ITodoType> yaziyorum. Bu birinci yol ama pek tercih edilmiyor.Yani bu sekilde type tanimlamasi yaptim aslinda.Ikinci yok ise useState<Array<ITodoType>>([]) . Ucuncu yol ve encok kullanilan yol useState<ITodoType[]>([])

16- .env.local dosyasini aciyorum vite_base_url dosyami olusturuyorum.

17- home icinde const url ile type string yapara env den import ediyorum. ve axios icine url yerlestiriyorum.settodos data olarak tyr icine yerlestiriyorum.catch kismina error console ekleyebilirim.

18- simdi use effect le home de gettodos u cagiriyorum.

19- addtodocomp u olusturdum.Burayi hazir olarak hoca  atti ve importlari sonra yapti. 2.04.06

20- kullanicin input a girdigi degeri yakalamam lazim.State e ihtiyacim var . State text yaparak initial e bos string veriyorum.Burada text uzerine mouse ile gelirsem type i string olarak gorecegim . TS inference ozelligi ile biz initial i bos string yaptigimiz  icin type string olarak belirled

21- textfield kismina onchange koyup settext i buraya e.traget.value olarak yerlestirdim.

22- Button a onclick oldugunda handleclick i cagir diyorum.Handleclick e addtodo fonksiyonu yaziyorum.Bu bana diger taraftada lazim olacagi icin addtodo yu bir ust olan home da yaziyorum . addtodo yu try catch ile yaziyorum.text parametresini async icine atarak type i string yapiyorum . Burada fonksiyona da type verebiliriz ama ts direk kendisi biz icine return koymadigimiz icin void olarak atadi ve async yaptigimiz icin bir promise olarak atadi.

23- Burada sunuda yapabilirim. bir type yazarim kendim. type AddFn = (text:string) => Promise<void> seklinde ve bundan sonra bunu asagida addToDo:AddFn seklinde belirtirsem yeterli olacaktir

24- try icinde axios.post u yazarim . finally kismini eklerim.

25- simdi bunu addtodo componentini yollarim.Componentin boyle bir seyden haberi yoksa direk kizaracak. addtodocomp icinde bunu destructuring ile cagiririm.sonra bunu handleclick icinde cagiririm.Input kismini tekrar sifirlamak icin setText i de bos string olarak bir kez daha yazarim.

26- Addtodocomp icinde bir interface tanimlayacagiz. Burada const ADDtodoComp icine yazdigim uzunyapiyi bu IAddtodocomp interface icine yazip daha okunakli hale getiriyorum.

27- button icine disable ozelligi veriyorum. !text.trim() vererek bos olarak calismasini engelliyorum.

28-src icinde types.d.ts diye bir sey aciyorum buraya yazdiklarimi ts global olarak algiliyor. Tekrar tekrar yazacagim seyleri buraya yazip diger yerlerde direk kuallaniyorum. Home.tsx icinde yazdigim type AddFn i buraya tasiyorum ve goruyorum ki bu component icinde AddFn i cagirmama ragmen hata almiyorum cunku global de yazdim az once.AddtodoComp icinde simdi bu AddFn yi direk cagiriyorum.

28- home.ts de toggletodo fonku addtodo yu kopyalayarak olusturuyorum.Tabiki bu axios.put olacak.Globalde toggleFn belirliyorum.Hatta interface ITodoType i da globale tasiyorum. Home da yazdigim toggle fonk icinde toolefn cagiridim.put icini duzenledim.Globalde DeleteFn belirledim.Yine kopyalama ile deleteTodo olusturdum Home.ts de.

29 - Todolisti duzenliorum. cons todolis icinde todos toggletodo deletetodo yu destructure ettim. interface imi yazdim.Todolist yanina React.FC yaziyorum. Bu return u kaldirdigim anda hata vermesini sagliyor.Artik burada returnun ici olan grid yapsini vs olusturuyorum.

30- todolist icinde progresstodo ve completedtodos u olusturuyorum.bunlari asagida typograph ler icinde cagiririyorum map ile bunlari geziyorum.Tabiki length 0 sa veya degilse seklinde sart kosuyroum.Tabiki probslari home.ts den todoliste gondermem lazim.

31- mui den listitem i kopyalayip todolist item a yapstiriyorum.importlari yapiyorum.interface aciyorum olusturuyorum. Todolistitem de destructuring  yaparak propslari karsiliyorum.primary kismina task ve todo olup olmamasi durumlarini yaziyorum ve buraya onclick toggletodoyu veriyorum. deletetodo yu deleteicon icinde koydugum onclick icine koyuyorum.Bu fonksiyonun icine parametresini yaziyorum. primary altina wordwrap yerlestiriyoum.

32- addtodocomp icinde textfield e inputprops vererek maxlength veriyorum ve karakter siralamsini olusturuyroum.

33- style.css dosyasini olusturuyorum.

34- sweetalert kismi icin pnpm add sweetalert2 ile kuruyorum ve helper dosyasi acarak bunun icine ilgili dokumandan copy paste yapiyorum.Burada enum kullandim.Home.ts de addtodo icinde notify koyarak sweetalerti ayarliyorum 
