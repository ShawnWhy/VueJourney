  
<template> 
<div id="app" v-cloak>
  <div style="z-index:99999;position:absolute;text-align:center; top:50px; width:100%">
  <input id = "nameInput" @keyup.enter="startJourney" v-model="name" placeholder="Please Submit Your Name">
  </div>
  <div v-show ="journey.start" id = "longLength">
   <div class = "sectionOne section">
    <div v-for = "(element,index) in starPieces[0]" v-bind:class = "[ { starFollow : stars[0]} , 'star']"></div>
    <div v-if="journey.start" class=" sectionHori sectionHori1">hello {{ name }}</div>
    <div v-if="journey.start" class="sectionHori sectionHori2">welcome </div>
    <div v-if="journey.start" class="sectionHori sectionHori3">please scroll down</div>
  </div>
  <div class="sectionTwo section" ref="sectionTwo">
        <div v-for = "(element,index) in starPieces[1]" v-bind:class = "[ { starFollow : stars[1]} , 'star']"></div>

     <div v-if="journey.sectionTwo" class="monitor">
        <div v-for="(component) in capturedResponse.articles" class = "screen" style="display:none">
         <img class="newsImage" v-bind:style="{backgroundImage:'url('+component.image+')'}">
          <div class="newsText"><h4>{{component.title}}</h4><p class="newsedscription">{{component.description}}</p></div>
          </div>
        <div class = "forward newsButton" @click="moveForward"><div> &lt;</div></div>
         <div class = "backwards newsButton" @click="moveBackwards"><div>&gt;</div></div>
      </div>
    <div v-for = "(index) in screenStripes.Hori" v-if= "journey.sectionTwo" class="sectionHori-2" 
    v-bind:style = "{top:index.top, transform:index.ani,zIndex:index.zIndex}"></div>
   <div v-for = "(index) in screenStripes.Vert" v-if= "journey.sectionTwo" class="sectionVert-2" 
  v-bind:style = "{left:index.left, transform:index.ani,zIndex:index.zIndex}"></div>
  </div>
  <div class="sectionThree section" ref="sectionThree">
  <div v-for="(element,index) in starPieces[2]" v-bind:class="[ { starFollow : stars[2]} , 'star']"></div>
  <div v-bind:style="{transform:cannonRotation}" style="left:20%" class="cannon">
    <div v-if="cannonParts.one[0]" class="cannonParts">
      <div v-if="cannonParts.one[1]" class="cannonParts">
        <div v-if="cannonParts.one[2]" class="cannonParts"></div>
    </div>
</div>
</div>
  <div v-bind:style="{transform:cannonRotation2}" style="left:40%" class="cannon">
    <div v-if="cannonParts.two[0]" class="cannonParts">
      <div v-if="cannonParts.two[1]" class="cannonParts">
        <div v-if="cannonParts.two[2]" class="cannonParts"></div>
    </div>
</div>
</div>
  <div v-bind:style="{transform:cannonRotation3}" style="left:60%"  class="cannon">
    <div v-if="cannonParts.three[0]" class="cannonParts">
      <div v-if="cannonParts.three[1]" class="cannonParts">
        <div v-if="cannonParts.three[2]" class="cannonParts"></div>
    </div>
  </div>
  </div>
<div v-if="cannonParts.one[2]" class="fireButton" @click="fireCannon"><div style="color:white;width:100%;text-align:center;position:absolute;top:40%;">FIRE!</div></div>
  <!-- <div class="sectionHori sectionHori2"></div>
  <div class="sectionHori sectionHori3"></div> -->

  </div>
  <div class = "sectionFour section" ref = "sectionFour">
  <div v-for = "(element,index) in starPieces[3]" v-bind:class = "[ { starFollow : stars[3]} , 'star']"></div>

  <div class = "catPictureContainer" ><img class="catPic"></div>
  <div class = "flipScreen">
  <div v-for = "(element, index) in screenFlips" V-bind:class = "[element]" V-bind:id = "[index]"></div>

</div>



  </div>

  </div>
    </div>
</template>   
    

    <script>
      // import Vue from 'vue'


      export default {
         created () {
        window.addEventListener('scroll', this.handleScroll);
        window.addEventListener('mousemove', event=>{this.starFollow(event)});
        


        this.getNews()
        
          },
        data() {
          return {

  newsIndex : 0,
  //   var newMeteor = $('<div>');

  // $(newMeteor).addClass('meteor');
  // $(newMeteor).attr("style", "background-image:linear-gradient(to top, rgba("+red+","+green+","+blue+",.4), rgba("+red+","+green+","+blue+",0)); right:"+width+"%; width:"+size+"px")

  capturedResponse:
  {
    "totalArticles": 297356,
    "articles": [
    {
    "title": "Vekker oppsikt internasjonalt",
    "description": "Norges protest blir lagt merke til.",
    "content": "Gibraltar - Norge 0-3\nNorge protesterte mot VM i Qatar før kveldens seier mot Gibraltar.\nStåle Solbakken hadde på seg en T-skjorte hvor det sto «Respect on and off the pitch», mens spillerne brukte t-skjorter med «Human rights on and off the pitch» u... [578 chars]",
    "url": "https://www.dagbladet.no/sport/vekker-oppsikt-internasjonalt/73570276",
    "image": "https://www.dagbladet.no/images/73570596.jpg?imageId=73570596&panow=100&panoh=100&panox=0&panoy=0&heightw=100&heighth=100&heightx=0&heighty=0&width=1200&height=630",
    "publishedAt": "2021-03-24T21:46:51Z",
    "source": {
    "name": "Dagbladet.no",
    "url": "https://www.dagbladet.no"
    }
    },
    {
    "title": "Massive container ship blocking Suez Canal paralyses trade for second day",
    "description": "The Ever Given was grounded early Tuesday amid poor visibility caused by a dust storm and wind speeds that reached 40 knots.. Read more at straitstimes.com.",
    "content": "CAIRO (BLOOMBERG) - Tugs and diggers have so far failed to dislodge a massive container ship stuck in the Suez Canal on Wednesday (March 24), increasing the chances of prolonged delays in what is arguably the world’s most important waterway.\nWork to ... [5274 chars]",
    "url": "https://www.straitstimes.com/world/suez-canal-stays-blocked-as-efforts-to-dislodge-stuck-container-ship-continues",
    "image": "https://www.straitstimes.com/s3/files/styles/x_large/public/articles/2021/03/24/ak_eg3_2403.jpg?itok=byer4se2",
    "publishedAt": "2021-03-24T21:42:43Z",
    "source": {
    "name": "The Straits Times",
    "url": "https://www.straitstimes.com"
    }
    },
    {
    "title": "Momentum builds within Liberal party to consider quotas for women even as divisions emerge",
    "description": "Defence industry minister Melissa Price says ‘the time has come’ for some kind of quota system to attract ‘qualified and motivated women’",
    "content": "The federal social services minister, Anne Ruston, has pushed back against growing calls within her own party for the Liberals to adopt a quota system for women, saying politicians should not “dictate” decisions in a democratic party.\nBut the push fo... [5994 chars]",
    "url": "https://www.theguardian.com/australia-news/2021/mar/25/momentum-builds-within-liberal-party-to-consider-quotas-for-women-even-as-divisions-emerge",
    "image": "https://i.guim.co.uk/img/media/c0f355857d161df4f33a95e37e6ff66311c7fe9c/0_65_3320_1993/master/3320.jpg?width=1200&height=630&quality=85&auto=format&fit=crop&overlay-align=bottom%2Cleft&overlay-width=100p&overlay-base64=L2ltZy9zdGF0aWMvb3ZlcmxheXMvdGctZGVmYXVsdC5wbmc&enable=upscale&s=a1a5792bbfa5168e120bc427ca891822",
    "publishedAt": "2021-03-24T21:39:00Z",
    "source": {
    "name": "The Guardian",
    "url": "https://www.theguardian.com"
    }
    },
    {
    "title": "Målløs Haaland da Norge slo miniputten Gibraltar",
    "description": "Erling Braut Haaland måtte gå målløs av banen da Norge enkelt slo Gibraltar.",
    "content": "Erling Braut Haaland måtte gå målløs av banen da Norge enkelt slo Gibraltar.\nGibraltar – Norge 0–3 (0–2)\nDet ble en frustrerende førsteomgang for landslaget, men like før pause løsnet det endelig.\nGibraltars keeper Dayle Coleing sto som en levende ve... [3793 chars]",
    "url": "https://www.tv2.no/a/13908592/",
    "image": "https://www.cdn.tv2.no/images/13908893.jpg?imageId=13908893&panow=100.00514208145&panoh=51.02813877551&panox=0.0051420814479575&panoy=17.006802721088&heightw=40.77740944206&heighth=100.0073316129&heightx=16.309012875536&heighty=0.0073316129032169&width=1200&height=630",
    "publishedAt": "2021-03-24T21:37:39Z",
    "source": {
    "name": "TV 2",
    "url": "https://www.tv2.no"
    }
    },
    {
    "title": "DOH wants vaccine line-jumpers punished; 5 mayors must explain",
    "description": "The Department of Health (DOH) urged the public on Wednesday to watch closely the vaccination process to make sure that only people on the government’s priority list get shots against COVID-19 as the home affairs office ordered five mayors to explain why they were inoculated ahead of their turn to be vaccinated.",
    "content": "MANILA, Philippines — The Department of Health (DOH) urged the public on Wednesday to watch closely the vaccination process to make sure that only people on the government’s priority list get shots against COVID-19 as the home affairs office ordered ... [7676 chars]",
    "url": "https://newsinfo.inquirer.net/1411062/doh-wants-vaccine-line-jumpers-punished-5-mayors-must-explain",
    "image": "https://newsinfo.inquirer.net/files/2021/03/News135352-620x351.jpg",
    "publishedAt": "2021-03-24T21:34:00Z",
    "source": {
    "name": "INQUIRER.net",
    "url": "https://newsinfo.inquirer.net"
    }
    },
    {
    "title": "Isro’s Chandrayaan-3 launch next year: Govt",
    "description": "The space agency earlier planned to launch the Chandrayaan 3 mission either in late 2020 or early 2021. However, most missions were rescheduled due to the Covid-19 pandemic.",
    "content": "The Indian Space Research Organisation (Isro) plans to launch its third mission to the Moon next year, the government said on Wednesday. In a written response to a question in the Lok Sabha, minister of state for the department of space, Jitendra Sin... [2821 chars]",
    "url": "https://www.hindustantimes.com/india-news/isros-chandrayaan-3-launch-next-year-govt-101616619292766.html",
    "image": "https://images.hindustantimes.com/img/2021/03/24/1600x900/_326c0358-2d6e-11eb-b9a2-d7de0b3760e9_1616621108852.png",
    "publishedAt": "2021-03-24T21:26:40Z",
    "source": {
    "name": "Hindustan Times",
    "url": "https://www.hindustantimes.com"
    }
    },
    {
    "title": "Hernando de Soto",
    "description": "“He logrado hacerlo sin quitarle ninguna vacuna a mis compatriotas”, dijo el candidato presidencial de Avanza País a su llegada a Cusco la tarde de este miércoles.",
    "content": "Conforme a los criterios de Saber más\nLuego de que las especulaciones crecieran en redes sociales, el candidato presidencial Hernando de Soto, de Avanza País, admitió este miércoles que se ha vacunado contra el COVID-19 durante sus recientes viajes a... [6917 chars]",
    "url": "https://elcomercio.pe/politica/elecciones/elecciones-2021-hernando-de-soto-confirma-que-se-vacuno-contra-la-covid-19-en-estados-unidos-avanza-pais-covid-19-noticia/",
    "image": "https://elcomercio.pe/resizer/XEOG-nQdIs57-Q79bfwZxC4UF24=/980x528/smart/filters:format(jpeg):quality(75)/cloudfront-us-east-1.images.arcpublishing.com/elcomercio/2KRYGKM3JRCB3FWD3UYQ27NRKM.jpg",
    "publishedAt": "2021-03-24T21:09:34Z",
    "source": {
    "name": "El Comercio Perú",
    "url": "https://elcomercio.pe"
    }
    },
    {
    "title": "Jennifer Lopez og Alex Rodriguez:",
    "description": "Selv om Jennifer Lopez og Alex Rodriguez ikke har endt forholdet, skal de likevel ha sine utfordringer.",
    "content": "Tidligere i mars lyste skjermer verden over opp, da flere nettsteder kunne melde at Jennifer Lopez (51) og forloveden Alex Rodriguez (45) hadde brutt forlovelsen.\nDet viste seg imidlertid ikke å stemme, noe paret selv avkreftet.\n- Alle artiklene stem... [3713 chars]",
    "url": "https://www.seher.no/kjendis/gjor-alt-de-kan/73570236",
    "image": "https://www.seher.no/images/73570440.jpg?imageId=73570440&panow=100.00521284404&panoh=33.950166972477&panox=0.0052128440366909&panoy=5.5045871559633&heightw=100&heighth=100&heightx=0&heighty=0&width=1200&height=630",
    "publishedAt": "2021-03-24T21:08:17Z",
    "source": {
    "name": "Seoghør.no",
    "url": "https://www.seher.no"
    }
    },
    {
    "title": "Virginia Gov. Ralph Northam signs law abolishing death penalty",
    "description": "After centuries of carrying out executions, Virginia on Wednesday became the 23rd state to abolish the death penalty after Gov. Ralph Northam signed historic legislation into law that ends capital punishment in the commonwealth.",
    "content": "Gov. Ralph Northam walks past the holding cells next to the death chamber during a tour at the Greensville Correctional Center prior to signing a bill abolishing the state's death penalty in Jarratt, Virginia, on Wednesday, March 24.\n(CNN) —\nAfter ce... [5319 chars]",
    "url": "https://www.cnn.com/2021/03/24/politics/virginia-governor-signs-law-death-penalty/index.html",
    "image": "https://cdn.cnn.com/cnnnext/dam/assets/210324141323-01-northam-dealth-penalty-bill-0324-super-169.jpg",
    "publishedAt": "2021-03-24T21:04:00Z",
    "source": {
    "name": "CNN",
    "url": "https://www.cnn.com"
    }
    },
    {
    "title": "ההתרסקות של סער מוכיחה: יורשו של נתניהו יגיע מבית",
    "description": "יו\"ר תקווה חדשה, שמאגפת את ראש הממשלה מימין, קיווה לסיים עם יותר משישה מנדטים. מהלך לאיחוד עם בנט היה מעלה את הסיכויים להוצאת נתניהו מבלפור, אך התכתשות ביניהם הביאה לאיבוד קולות. ולמרות הכשלון, ישנה דרך נוספת שיכולה לשנות דרמטית את התמונה",
    "content": "רוב ראשי המפלגות ביקשו אמש (שלישי) להמתין לתוצאות הרשמיות בבחירות לכנסת ה-24, מרביתם גזרו על עצמם שתיקה זמנית אבל אחד מהם כבר הבין שהסיבוב הקרוב מבחינתו נגמר בהפסד. יו\"ר תקווה חדשה, גדעון סער, עמד אתמול בלילה על הבמה במטה המפלגה, והודה כי הייתה לו תק... [739 chars]",
    "url": "https://elections.walla.co.il/item/3425707",
    "image": "https://img.wcdn.co.il/f_auto,w_1200,t_54/ar_1.91,c_fill,g_auto/l_black_line,g_south,w_1.0,h_0.1,fl_relative,o_90/g_south_east,x_15,y_12,l_logo_2020,w_250/3/1/4/8/3148513-46.jpg",
    "publishedAt": "2021-03-24T21:02:20Z",
    "source": {
    "name": "וואלה!",
    "url": "https://elections.walla.co.il"
    }
    }
    ]
    },

      screenFlips:[
      "flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn",
      "flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn",
"flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn","flipOn",],
      flipTrigger:"on",


            stars:[false,false,false,false,],
            starPieces:[
            [1,2,3,4,5,6,7,8,9,10],
            [1,2,3,4,5,6,7,8,9,10],
            [1,2,3,4,5,6,7,8,9,10],
            [1,2,3,4,5,6,7,8,9,10],

              ],
            screenStripes:{
              Hori:{
                0:{ani:"translate(-100%)",top:"0px",zIndex:"0"},
                1:{ani:"translate(-100%)",top:"30px",zIndex:"1"},
                2:{ani:"translate(-100%)",top:"60px",zIndex:"2"},
                3:{ani:"translate(-100%)",top:"90px",zIndex:"3"},
                4:{ani:"translate(-100%)",top:"120px",zIndex:"4"},
                5:{ani:"translate(-100%)",top:"150px",zIndex:"5"},
                6:{ani:"translate(-100%)",top:"180px",zIndex:"6"},
                7:{ani:"translate(-100%)",top:"210px",zIndex:"7"},
                8:{ani:"translate(-100%)",top:"240px",zIndex:"8"},
                9:{ani:"translate(-100%)",top:"270px",zIndex:"9"},
                10:{ani:"translate(-100%)",top:"300px",zIndex:"10"},
                11:{ani:"translate(-100%)",top:"330px",zIndex:"11"},
                12:{ani:"translate(-100%)",top:"360px",zIndex:"12"},
                13:{ani:"translate(-100%)",top:"390px",zIndex:"13"},
                14:{ani:"translate(-100%)",top:"420px",zIndex:"14"},
                15:{ani:"translate(-100%)",top:"450px",zIndex:"15"},
              },
              Vert:{
                0:{ani:"translateY(-100%)",left:"0px",zIndex:0},
                1:{ani:"translateY(-100%)",left:"30px",zIndex:1},
                2:{ani:"translateY(-100%)",left:"60px",zIndex:2},
                3:{ani:"translateY(-100%)",left:"90px",zIndex:3},
                4:{ani:"translateY(-100%)",left:"120px",zIndex:4},
                5:{ani:"translateY(-100%)",left:"150px",zIndex:5},
                6:{ani:"translateY(-100%)",left:"180px",zIndex:6},
                7:{ani:"translateY(-100%)",left:"210px",zIndex:7},
                8:{ani:"translateY(-100%)",left:"240px",zIndex:8},
                9:{ani:"translateY(-100%)",left:"270px",zIndex:9},
                10:{ani:"translateY(-100%)",left:"300px",zIndex:10},
                11:{ani:"translateY(-100%)",left:"330px",zIndex:11},
                12:{ani:"translateY(-100%)",left:"360px",zIndex:12},
                13:{ani:"translateY(-100%)",left:"390px",zIndex:13},
                14:{ani:"translateY(-100%)",left:"420px",zIndex:14},
                15:{ani:"translateY(-100%)",left:"450px",zIndex:15},
            }



            },
          
            cannonRotation:'rotate(90deg)',
            cannonRotation2:'rotate(90deg)',
            cannonRotation3:'rotate(90deg)',    
            cannonParts:{
              one:[false, false, false],
              two:[false,false,false],
              three:[false, false, false]             
            },
            objctHeights:{
            
            },
            name:'',
            journey:{
              start:false,
              sectionTwo:false,
              sectionThree:false,
              sectionFour:false,
            },
            inventory: {
              carrots: 0,
              pineapples: 0,
              cherries: 0
            },
            cart: {
              carrots: 0,
              pineapples: 0,
              cherries: 0
            }
          }
        },
        methods: {
      starFollow(event){
        // console.log("starfollow")
        var mouseY=event.pageY+20
        var mousex=event.pageX+20
        var starsFollow =$('.starFollow')
        for(let i=0;i<starsFollow.length;i++){
          setTimeout(() => {
              $(starsFollow[i]).css("top",mouseY);
              $(starsFollow[i]).css("left",mousex)
            
          }, 200*i);
        }

      },
      //generateStars

      generateStars(section){
        console.log(section+" generate")
        var stars = $(section+" .star")
        console.log(stars)
        $(stars).removeClass("invisibleP")
        var starlengh=stars.length;
        for(let i=0; i<starlengh; i++){

        let randomTop = Math.random()*90+5;
        let randomleft = Math.random()*90+5;
        let randomWidth = Math.random()*50+5;
        function rdcolor(){let color;var letters = '0123456789ABCDEF';  color = '#';for (var j = 0; j < 6; j++){;color += letters[Math.floor(Math.random() * 16)]};return color}
        let randcolor=rdcolor()
        $(stars[i]).css("top",randomTop+"%")
        $(stars[i]).css("left",randomleft+"%")       
           $(stars[i]).css("width",randomWidth)


        $(stars[i]).html('<svg class="starbody'+i+'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 259.28 246.36"><defs><style>.cls-starbody'+i+'{fill:'+randcolor+'}</style></defs><polygon class="cls-starbody'+i+'" points="91.92 84.56 0 96.65 71.55 155.61 47.81 246.36 129.28 202.11 211.47 246.36 187.73 155.61 259.28 96.65 166.97 85.03 130.01 0 91.92 84.56"/></g></g></svg>');
      }      
      },

//       activateStars(section){
//       this.stars[section-1]=true


// },

      //this triggers the fourth section 
      SetupFlip(){
      var flips = $(".flipOn")
      function rdcolor(){var color;var letters = '0123456789ABCDEF';var color = '#';for (var j = 0; j < 6; j++){;color += letters[Math.floor(Math.random() * 16)]};return color}
      for(let i=0;i<flips.length-1;i++){
       let randColor = rdcolor;
      $(flips[i]).css("background-color",rdcolor)
      setTimeout(() => {
        $(flips[i]).css("transform","rotate3d(0,1,0,0deg)")
      }, i*10);  


        }
      //jquery into the on hover for the flippers
      $('.flipOn').mouseover(event=>{
          // console.log("hover")
        $(event.target).css("transform","rotate3d(0,1,0,90deg)")      
        })
      $(".catPictureContainer").click(event=>{
        this.generateStars(".sectionFour")})
        this.stars[3]=true;
      
      $.ajax({

        //gets teh cat images
        url: "https://api.thecatapi.com/v1/images/search",
        method:"GET"
        }).then(function(response) {
        if(response){ 
          console.log(response);
          var url = response[0].url
          var catPic = $(".catPic");
             $(catPic).attr("src", url) 
              $(catPic).css("visibility", "hidden") 

       
          setTimeout(() => {
            let containerHeight = $(".flipOn").outerHeight()*7;
            let imageHeight = $(".catPic").outerHeight();
            console.log("imageheight "+ imageHeight)
                        console.log("containerheight "+ containerHeight)

            let marginCat = containerHeight-imageHeight;
              if(marginCat>0){
                $(".catPic").css("top",marginCat/2+"px")
                }
              else{
                $(".catPic").css("height",containerHeight-10+"px")
                $(".catPic").css("top","5px")
                }
                $(".catPic").css("visibility", "visible")          

          }, 2000);
             
        }
        })
      
      this.flipTrigger="off"       
    },


      moveForward(){
      this.generateStars('.sectionTwo');
      console.log("forwad")
      let currentNews = $('.screen')
      let length = currentNews.length;
      this.newsIndex++;
        if(this.newsIndex>length-1){
      this.newsIndex=0  
      }
      console.log(this.newsIndex)
      console.log(currentNews[this.newsIndex])
      $(".screen").css("display","none");
      $(currentNews[this.newsIndex]).css("display","block")

      },


      moveBackwards(){
            this.generateStars('.sectionTwo');

      console.log("backwards")


      let currentNews = $('.screen')
      let length = currentNews.length;
      this.newsIndex--;
        if(this.newsIndex<0){
      this.newsIndex=length-1  
      
      }
      console.log(this.newsIndex)
console.log(currentNews[this.newsIndex])
      $(".screen").css("display","none");
      $(currentNews[this.newsIndex]).css("display","block")
      },

      getNews(){
        var APIKey= "61fec83c505722615ff089ec90d63d94";
        var queryURL = "https://gnews.io/api/v4/top-headlines?lang=en&token="+APIKey
        $.ajax({
        url: queryURL,
        method:"GET"
        }).then(function(response) {
        if(response){ this.capturedResponse = response;
          console.log("captured!");
        }
        })
        },
      
          rotatecannon(scrollY, cannonheight){
                let percentage = (scrollY-cannonheight)/300;
                // console.log(percentage)
                let degree = percentage*90
                console.log(degree)
                var raisedegree = 90 - degree
                if(raisedegree<0){
                radisdegree=0}
                this.cannonRotation = "rotate("+raisedegree.toString()+"deg)" 
                setTimeout(() => {
                this.cannonRotation2 = "rotate("+raisedegree.toString()+"deg)"
                  setTimeout(() => {
                this.cannonRotation3 = "rotate("+raisedegree.toString()+"deg)" 
      
                }, 200);    
                }, 200);
          },
              generateScreen(scrollY, screenHeight){
          let percentage = (scrollY-screenHeight)/100;
          percentage= percentage*100
          console.log("generateScreen")
          for(i=0; i<16; i++){ 
            let percentageAdd = -100+percentage-100*i/16
            if (percentageAdd > 0){
              percentageAdd = 0}
            else if(percentageAdd<-100){
                percentageAdd=-100

            }
            // console.log(this.screenStripes.hori[i])
            this.screenStripes.Hori[i].ani = "translate(" +percentageAdd.toString() +"%)"
            this.screenStripes.Vert[i].ani = "translateY(" +percentageAdd.toString() +"%)"

          }
          },


          startJourney(){
          console.log("start")
          this.journey.start=true;
          this.generateStars('.sectionOne');
          },
          addToCart(type) {
            this.cart[type] += this.inventory[type]
            console.log(this.cart)
          },
          handleScroll(){
            var scrollheight2 = this.$refs.sectionTwo.offsetTop
            var scrollheight3 = this.$refs.sectionThree.offsetTop
            var scrollheight4 = this.$refs.sectionFour.offsetTop

           if(window.scrollY>scrollheight2-400&&window.scrollY<scrollheight2){

                this.journey.sectionTwo=true;
                this.generateScreen(window.scrollY, scrollheight2-390)
                console.log("sec2") 
          }
          if(window.scrollY<scrollheight2-400){
              this.journey.sectionTwo=false;
                             this.stars[0]=true

              
              
            }
          if(window.scrollY>scrollheight3-700&&window.scrollY<scrollheight3-400){
                this.stars[1]=true
                this.journey.sectionThree=true;
                setTimeout(() => {
                  this.cannonParts.one[0]=true
                setTimeout(() => {
                  this.cannonParts.one[1]=true
                setTimeout(() => {
                  this.cannonParts.one[2]=true
                  
                }, 100);
                  
                }, 100);
                  
                }, 100);
               setTimeout(() => {
                  this.cannonParts.two[0]=true
                setTimeout(() => {
                  this.cannonParts.two[1]=true
                setTimeout(() => {
                  this.cannonParts.two[2]=true
                  
                }, 100);
                  
                }, 100);
                  
                }, 200);
                setTimeout(() => {
                  this.cannonParts.three[0]=true
                setTimeout(() => {
                  this.cannonParts.three[1]=true
                setTimeout(() => {
                  this.cannonParts.three[2]=true
                  
                }, 100);
                  
                }, 100);
                  
                }, 300);
                // alert(window.scrollY)
                // alert(scrollheight3+100)
                this.rotatecannon(window.scrollY, scrollheight3-700)

          }
          if(scrollY<scrollheight3-700){
                  
                  this.cannonParts.one[2]=false
                setTimeout(() => {
                  this.cannonParts.one[1]=false
                setTimeout(() => {
                  this.cannonParts.one[0]=false
                  
                }, 100);
                  
                }, 100);
                  
                
               setTimeout(() => {
                  this.cannonParts.two[2]=false
                setTimeout(() => {
                  this.cannonParts.two[1]=false
                setTimeout(() => {
                  this.cannonParts.two[0]=false
                  
                }, 100);
                  
                }, 100);
                  
                }, 100);
                setTimeout(() => {
                  this.cannonParts.three[2]=false
                setTimeout(() => {
                  this.cannonParts.three[1]=false
                setTimeout(() => {
                  this.cannonParts.three[0]=false
                  
                }, 100);
                  
                }, 100);
                  
                }, 200);


          }
          if(scrollY>scrollheight4-400){
                          this.stars[2]=true

          }

          if(scrollY>scrollheight4-100){
              if(this.flipTrigger=="on"){
              this.SetupFlip()}
          }
        },
          fireCannon(){
            function rdcolor(){var color;var letters = '0123456789ABCDEF';var color = '#';for (var j = 0; j < 6; j++){;color += letters[Math.floor(Math.random() * 16)]};return color}
            var color = rdcolor();
            console.log("firecannon!")
            $(".cannonBall").remove();
            var cannonBall = $('<div>')
            $(cannonBall).addClass("cannonBall");
            $(cannonBall).css("background-color",color)
            console.log($)
            console.log(cannonBall)
            var cannonBall2 = $('<div>')
            $(cannonBall2).addClass("cannonBall");
            $(cannonBall2).css("background-color",color)
            console.log($)
            console.log(cannonBall)
            var cannonBall3 = $('<div>')
            $(cannonBall3).addClass("cannonBall");
            $(cannonBall3).css("background-color",color)
            console.log($)
            console.log(cannonBall)
            var cannons = $(".cannon")
            $(cannons[0]).append(cannonBall);

              setTimeout(() => {
              for(i=0; i<8; i++){
              var cannonPiece = $('<div>')
              let randTurn = Math.floor(Math.random()*7+1)
              $(cannonPiece).addClass("cannonPiece");
              $(cannonPiece).css("animation","cannonExplode"+randTurn.toString()+" .2s both");
              $(cannonPiece).css("background-color",color)
              var cannonballs = $(".cannonBall");
              $(cannonballs[0]).append(cannonPiece)}
                setTimeout(() => {
                              this.generateStars(".sectionThree")

                }, 100);
                
              }, 400);
            setTimeout(() => {
              $(cannons[1]).append(cannonBall2);
                   setTimeout(() => {
              for(i=0; i<8; i++){
              var cannonPiece = $('<div>')
              let randTurn = Math.floor(Math.random()*7+1)
              $(cannonPiece).addClass("cannonPiece");
              $(cannonPiece).css("animation","cannonExplode"+randTurn.toString()+" .2s both");
              $(cannonPiece).css("background-color",color)
              var cannonballs = $(".cannonBall");
              $(cannonballs[1]).append(cannonPiece)}
              setTimeout(() => {
                              this.generateStars(".sectionThree")

                }, 100);
                
              }, 400);
              setTimeout(() => {
              $(cannons[2]).append(cannonBall3);
                     setTimeout(() => {
              for(i=0; i<8; i++){
              var cannonPiece = $('<div>')
              let randTurn = Math.floor(Math.random()*7+1)
              $(cannonPiece).addClass("cannonPiece");
              $(cannonPiece).css("animation","cannonExplode"+randTurn.toString()+" .2s both");
              $(cannonPiece).css("background-color",color)
              var cannonballs = $(".cannonBall");
              $(cannonballs[2]).append(cannonPiece)}
                   setTimeout(() => {
                              this.generateStars(".sectionThree")

                }, 100);
                
              }, 400);
            }, 200);
            }, 200);
            // $(".cannon")[2].append(cannonBall);


        }
        }
      }

      // app.mount('#app')
    </script>
    <style>
.sectionTwo{
width:483.12px !important;
margin:auto;
}


.sectionHori {
    position:absolute;
    text-align:center;
    font-size: xx-large;

    border-radius:30px;
    padding:10px;
    background-color:orange;
    color:white;

    float:right;
    width:50%;
    margin:2%;
}
.sectionHori-2 {
    border-radius:20px;
    padding:10px;
    background-color:rgb(0, 140, 255);
    color:white;
    position:absolute;

    float:right;
    width:100%;
    height:15px;
}

.star{
position:absolute;
z-index:0;

}

.starFollow {
transform-origin: center;
animation:starSpin .5s infinite linear;


}
@keyframes starSpin {
0%{transform:rotate(0deg)}
100%{transform:rotate(360deg)}

  
}

.sectionVert-2 {
    border-radius:30px;
    padding:10px;
    background-color:orange;
    color:white;
    position:absolute;

    float:right;
    height:59%;
    width:15px;
}




.sectionHori1 {

top:10%;
animation:fromLeft .2s both;


}
.sectionHori2 {
top:20%;
animation:fromLeft .2s both;
animation-delay:.2s

}

.sectionHori3 {
top:30%;   
animation:fromLeft .2s both;
animation-delay:.4s
}

@keyframes fromLeft{
0%{transform:translateX(-300%)}
100%{transform:translateX(50%)}
}


#longLength{
    background-image: linear-gradient(to bottom, green, pink, orange, lightblue);
    height: 3200px;
    overflow:hidden;

}

#nameInput{
position:relative;
border-radius:10px;
margin:auto;
z-index:9999;
padding:10px;
}

.section{
height:25%;
position:relative;
width:100%;
}

  .cannon{
height:15%;
position:absolute;
text-align:right;
width:4%;
top:15%;
background-color: black;
transform-origin: bottom;
border-radius: 0px 0px 50px 50px;


  }
.cannonParts{
background-color: black;
width:95%;
height:50%;
margin:auto;
animation:cannonPartsActivate .1s both

}

@keyframes cannonPartsActivate {
0%{transform:translateY(0%)}
100%{transform:translateY(-50%)}
    
}

.cannonBall{
 width:80%;
 padding-bottom:80%;
border-radius:50%;
position:absolute;
left:10%;
top:-50%;
z-index:-4;
animation:shootCannon .5s both;
}

@keyframes shootCannon {
0%{transform:translate(0%, 0%);}
99%{transform:translate(50% ,-800%)}
100%{transform:translate(50% ,-800% );visibility: hidden;}
}

.cannonPiece{
 width:40%;
 padding-bottom:40%;
border-radius:50%;
position:absolute;
z-index:-4;
}

.fireButton{
 width:5%;
 padding-bottom:5%;
background-color: rgb(35, 35, 92);
border-radius:30%;
animation:fireButton .2s both;
transform-origin:center;
position:absolute;
left:80%;
top:10%;
text-align: center;
font-weight:600;
}
@keyframes fireButton{
0%{
transform:scale(10%);

}
100%{
transform:scale(100%);

}
}
.fireButton:hover{
background-color: rgb(255, 0, 191);
}
@keyframes cannonExplode1 {
0%{transform:rotate(10deg)translate(0%);}
99%{transform:rotate(10deg)translate(-800%)}
100%{transform:rotate(10deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode2 {
0%{transform:rotate(30deg)translate(0%);}
99%{transform:rotate(30deg)translate(-800%)}
100%{transform:rotate(30deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode3 {
0%{transform:rotate(270deg)translate(0%);}
99%{transform:rotate(270deg)translate(-800%)}
100%{transform:rotate(270deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode4 {
0%{transform:rotate(300deg)translate(0%);}
99%{transform:rotate(300deg)translate(-800%)}
100%{transform:rotate(300deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode5 {
0%{transform:rotate(96deg)translate(0%);}
99%{transform:rotate(96deg)translate(-800%)}
100%{transform:rotate(96deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode6 {
0%{transform:rotate(55deg)translate(0%);}
99%{transform:rotate(55deg)translate(-800%)}
100%{transform:rotate(55deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode7 {
0%{transform:rotate(110deg)translate(0%);}
99%{transform:rotate(110deg)translate(-800%)}
100%{transform:rotate(110deg)translate(-800% );visibility: hidden;}
}
@keyframes cannonExplode8 {
0%{transform:rotate(75deg)translate(0%);}
99%{transform:rotate(75deg)translate(-800%)}
100%{transform:rotate(75deg)translate(-800% );visibility: hidden;}
}

.monitor{
position:absolute;
z-index:999;
height:40%;
top:3%;
left:10%;
width:80%;
border-radius:40px;
background: radial-gradient(blue, orange);
animation:fireButton .3s both;
}
.newsButton{
height:100%

}
.newsButton div{
position:relative;
padding:5%;
top:50%;
font-weight:900;
color:white;
margin:auto;
border-radius:3px;

}
.forward{
width:5%;
position:absolute;


}

.backwards{
width:5%;
position:absolute;
left:95%;
}



.forward :hover{
background-color: orange;
}

.backwards :hover{
background-color: blue;
}

.newsImage{
position:absolute;
height:50%;
width:90%;
left:5%;
background-size: cover;
border-radius: 30px;
}
.newsText{
position:absolute;
top:50%;
padding:10px;


}
.flipScreen{
perspective:9999999px;
width:100%;
transform-style: preserve-3d;
z-index:1

}
.flipOn{
float:left;
 width:5%;
 padding-bottom:5%;
border-radius:3px;
transform-style:preserve-3d;
transition:transform .3s,  background-color .3s;
transform:rotate3d(0,1,0,90deg)

}

.catPictureContainer{
position:absolute;
margin:auto;
z-index:0;
width:100%;
height:35%;
text-align:center;

}
.catPic{
position:relative;
margin:auto;
max-width:50%;
border-radius: 10px;
max-height:400px;

}
.invisibleP{
position:absolute;
display:none;


}
    
    </style>