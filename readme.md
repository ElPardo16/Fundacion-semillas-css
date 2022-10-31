# Documentacion

Se hizo una estructura basica de archivos sobre los que ibamos a trabajar.

En el css general se agregaron estilos que compartirian todas las paginas como estos:



        @import url('https://fonts.googleapis.com/css2?family=Dosis&family=Playfair+Display&display=swap');
        *{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        h1, h2{
            font-family: var(--playfair);
        }
        p{
            font-family: var(--dosis);
        }


Ademas se crearon variables con los colores y fuentes


        :root{
        --accent : #009458;
        --dark: #0b3d26;
        --hover : #69bf97;
        --gris : #ededed;
        --dosis: 'Dosis', sans-serif;
        --playfair: 'Playfair Display', serif;
        }


### Header

<img src="./src/img/d1.png" width="700px" alt="logo">


Se comenzo desarrollando el header y el footer ya que todas las paginas lo tenian, entonces sus estilos se agregaron en "general.css" ademas de su responsive.

<img src="./src/img/d1-2.png" width="200px" alt="logo">

### Pagina home

En esta pagina solo se agregaron dos contenedores, que son los botones principales


        <div class="card">
            <a href="./students.html"><img src="./src/img/niños.jpeg" alt="Imagen card" srcset=""></a>
            <h1>Lista De Estudiantes </h1>
        </div>

Ademas de un hover con una animacion, que se hizo con un pseudoelemento, una transformacion y una transicion


        .card a::before{
            position: absolute;
            content: "";
            inset: 0;
            margin: auto;
            background: var(--hover);
            width: 100%;
            height: 0%;
            opacity: .6;
            filter: brightness(150%);
            transition: all ease .3s;
        }

        .card a:hover h1{
            transform: scale(1.2);
        }

Solo se usaron 3 mediaquerys para el responsive


        @media (max-width: 480px) /*Mobile*/

        @media (min-width: 481px) and (max-width: 1000px) /*Tablet*/
    
        @media (max-width: 1000px) /*Mobile y Tablet estilos compartidos*/

### Animaciones

Para realizar las animaciones se usaron:
 
- keyframes
- transition
- animation

Por ejemplo para esta animacion de la cara que cambia de tamaño se uso un keyframe y la propiedad animation con un valor infinite para que siempre se ejecute

<img src="./src/img/d3.png" width="200px" alt="logo">


        @keyframes escalar {
            0%{
                transform: scale(1)
            }
            50%{
                transform: scale(1.2)
            }
            100%{
                transform: scale(1)
            }
        }
        /*En el objeto*/

        animation: escalar 1.8s ease infinite;


### Dinamismo

Para emular algunas acciones que deberian ser hechas con javascript o un backend se hizo uso de las "Custom Propertys" y algunos trucos de css. 
Se usaron en los checkbox para cambiar la calificacion y en el menu de seleccion de materias para cambiar los textos y las graficas 

Aunque estos tienen usos bastante limitados a comparacion de un lenguaje de programacion y requieren de un codigo extenso y poco escalable.

como veremos a continuacion se usaron estas propiedades solo para el menu:

        :root{
            --titulo_m: "Reciclaje";
            --w1: 85%;
            --w2: 70%;
            --w3: 81%;
            --w4: 35%;
            --w5: 25%;
            --t1: "85%";
            --t2: "70%";
            --t3: "81%";
            --t4: "35%";
            --t5: "25%";
            --cr: rotate(0);
        }

las cuales cambiaban su valor cuando se hacia un hover, checked o un target


        #m2:target{
            --titulo_m: "Cartografia";
            --w1: 65%;
            --w2: 70%;
            --w3: 90%;
            --w4: 55%;
            --w5: 75%;
            --t1: "65%";
            --t2: "70%";
            --t3: "90%";
            --t4: "55%";
            --t5: "75%";
            --cr: rotate(30deg);
        }


### Lista de estudiantes

Para la lista de estudiantes se uso un sidebar con la etiqueta aside, en el contenedor usamos una imagnes y un texto para representar la foto y el nombre del estudiante

        <aside>
             <h1>Lista de estudiantes</h1>
                <ul>
                    <li class="select"><a href="#jay">
                        <img src="./src/img/s3.png" alt="student - Jay">
                        <p>Jay Jonson</p>
                    </a></li>
                    <li><a href="#Jhon">
                        <img src="./src/img/s6.png" alt="student - Jhon">
                        <p>Jhon Doe</p>
                    </a></li>
                    <li><a href="#Jacobo">
                        <img src="./src/img/s1.png" alt="student - Jacobo">
                        <p>Jacobo Bans</p>
                    </a></li>
                    <li><a href="#Mariana">
                        <img src="./src/img/s4.png" alt="student - Mariana">
                        <p>Mariana Celis</p>
                    </a></li>
                    <li><a href="#Lucia">
                        <img src="./src/img/s2.png" alt="student - Lucia">
                        <p>Lucia Derlys</p>
                    </a></li>
                    <li><a href="#Mia">
                        <img src="./src/img/s5.png" alt="student - Mia">
                        <p>Mia Claudia</p>
                    </a></li>
                </ul>
            </aside>

![image](https://user-images.githubusercontent.com/50422794/199070669-144fbad1-6b51-4341-a784-e20ca554522c.png)

En la animacion al momento de pasar el cursor por cada seccion de las diferentes imagenes se utilizo la propiedad hover en el css, de esta forma se añade un color de forma horizontar de izquierda a derecha y se cambia el tamaño tanto de la imagen como del texto

        aside ul li:before{
            content: "";
            width: 100%;
            height: 100%;
            background: var(--accent);
            position: absolute;
            top: 0;
            left: -100%;
            transition: all ease .3s;
        }
        aside ul li:hover::before{
            left: 0;
        }
        /*aside ul li:hover{
            background: var(--accent);
        }*/
        .select{
            background: var(--accent);
        }
        aside ul li a{
            position: relative;
            display: flex; 
            justify-content: flex-start; 
            gap: 30px;
            align-items: center;
            padding-left: 20px;
            width: 100%;
            height: 100%;
            z-index: 10;
            transition: all ease .3s;
        }
        aside ul li a:hover{
            transform-origin: 0 50%;
            transform: scale(1.2);
        }
        
![image](https://user-images.githubusercontent.com/50422794/199072269-ecbf14f5-af79-490e-84d0-b4b2dfcdf73f.png)

Para el listado de tareas utilizamos una etiqueta section, con 2 contenedores, uno para la barra principal y otro para el contenido
        
            <section>
                <div class="card card-info">...</div>
                <div class="card materias">
                    <div class="lista">
                        <ul>
                            <li><a href="#">Reciclaje</a></li>
                            <li><a href="#m2">Cartografia</a></li>
                            <li><a href="#m3">Ecologia del paisaje I</a></li>
                        </ul>
                    </div>
                </div>
            </section>

![image](https://user-images.githubusercontent.com/50422794/199074074-905114f2-3361-40db-8aae-c13d97016b39.png)

        #m2:target{
            --titulo_m: "Cartografia";
            --w1: 65%;
            --w2: 70%;
            --w3: 90%;
            --w4: 55%;
            --w5: 75%;
            --t1: "65%";
            --t2: "70%";
            --t3: "90%";
            --t4: "55%";
            --t5: "75%";
            --cr: rotate(30deg);
        }
        #m3:target{
            --titulo_m: "Ecologia del paisaje I";
            --w1: 15%;
            --w2: 90%;
            --w3: 60%;
            --w4: 35%;
            --w5: 75%;
            --t1: "15%";
            --t2: "90%";
            --t3: "60%";
            --t4: "35%";
            --t5: "75%";
            --cr: rotate(-30deg);
        }
        .card{
                border-radius: 20px;
                background: var(--dark);
            color: white;
            box-shadow: rgba(0, 0, 0, .6) 3px 3px 7px;
        }
        section > h1{
                padding: 20px 0;
                color: var(--accent);
                text-align: center;
        }
        .materias{
                min-height: 40px;
                position: relative;
                --r: rotate(180deg);
                --h: hidden;
                --t: scaleY(0);
                overflow: var(--h);
        }
        .materias:hover{
                --h: normal;
                --t: scaleY(1);
                --r: rotate(0);
        }
        .materias::before{
                content: var(--titulo_m);
                padding: 15px 30px;
                display: block;
                font-size: 1.4rem;
                font-weight: bold;
                font-family: var(--dosis);
                letter-spacing: 1px;
        }
        .materias::after{
                content: "";
                position: absolute;
                width: 0; height: 0;
                border-top: 0 solid transparent;
                border: 10px solid transparent;
                border-bottom: 10px solid white;
                inset: 0;
                margin: auto;
                margin-right: 30px;
                transform: var(--r);
                transition: all ease .4s;
        }
        .lista ul{
                position: absolute;
                height: 300%;
                width: 90%;
                top: 100%; 
                left: 0; right: 0;
                background: var(--accent);
                display: grid;
                grid: repeat(3,1fr) / 1fr;
                justify-items: start;
                margin: 0 auto;
                transition: all ease .4s;
                z-index: 100;
            transform: var(--t);
            transform-origin: 0 0;
            font-family: var(--dosis);
        }
        .lista ul li{
                line-height: 50px;
                padding-left: 30px;
            display: block;
            width: 100%;
        }
        .lista a{
            color:white;
            display: block;
        }
        .lista li:hover{
            background: var(--gris);
        }
        .lista li:hover a{
            color: var(--accent);
        }

![image](https://user-images.githubusercontent.com/50422794/199074165-449c749c-7197-41eb-95ee-95147b2490a8.png)

En las cards donde se muestra avance, estado de animo, calificaciones y demas, añadimos una clase base

        <main>
            <section>
                <div class="card card-info">
                    <img src="./src/img/s3.png" alt="">
                    <div class="card__texto">
                        <h1>Jay Jonson</h1>
                        <p>Ingenieria Ambiental</p>
                    </div>
                </div>
                <h1>Materias</h1>
                <div class="card materias">
                    <div class="lista">
                        <ul>
                            <li><a href="#">Reciclaje</a></li>
                            <li><a href="#m2">Cartografia</a></li>
                            <li><a href="#m3">Ecologia del paisaje I</a></li>
                        </ul>
                    </div>
                </div>
            </section>
            <section class="bars">
                <div class="card stats">
                    <h1>Notas</h1>
                    <div class="grafica1">
                        <div class="bar" data-text="85%"></div>
                        <div class="bar" data-text="70%"></div>
                        <div class="bar" data-text="81%"></div>
                        <div class="bar" data-text="35%"></div>
                        <div class="bar" data-text="25%"></div>
                    </div>
                    <p>Calificaciones de los tabajos asignados por el docente</p>
                </div>
                <div class="card stats">
                    <h1>Habilidad</h1>
                    <div class="grafica2">
                        <div>
                            <div class="cicle"></div>
                        </div>
                    </div>
                    <p>Capacidad de desarrollar los trabajos con calidad</p>
                </div>
                <div class="card stats">
                    <h1>Estado de animo</h1>
                    <div class="grafica3">
                        <div class="face"></div>
                        <div class="face"></div>
                        <div class="face"></div>
                    </div>
                    <p>Estado de animo con respecto a la clase</p>
                </div>
            </section>
            <div class="card progresoG">
                <h1>Progreso General</h1>
                <div class="triangulo" data-text="70%">
                    
                </div>
                <p>Progreso comparado con el promedio de los estudiantes</p>
            </div>
        </main>

y se agregaron varias animaciones para cada seccion de estado

        .bars{
                display: grid;
                grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
                padding: 50px 20px;
                gap: 40px;
                place-items: strech;
        }

        .stats{
                padding: 30px 40px;
                display: flex;
                flex-direction: column;
            align-items: center;
                gap: 30px;
        }

        .stats > h1{
                text-align: center;
        }

        .stats > div{
            width: 160px;
                height: 160px;
                position: relative;
        }

        .grafica1{
                display: grid;
                grid: repeat(5, 1fr) / 1fr;
                gap: 5px;
                padding: 20px 0;
        }

        .bar{
                background: rgba(0, 0, 0, .6);
                position: relative;
                height: 100%;
                width: 100%;
        }

        .bar::before{
                content: "";
                color: white;
                position: absolute;
                left: 0; top: 0;
                height: 100%;
                width: 80%;
                text-align: right;
                padding: 0 5px;
            transform-origin: 0% 0%;
            animation: llenar 2s ease;
                font-family: var(--dosis);
        }

        .bar:nth-child(1)::before{
            content: var(--t1);
                width: var(--w1);
            background: rgb(199, 26, 26);
        }
        .bar:nth-child(2)::before{
            content: var(--t2);
                width: var(--w2);
            background: rgb(22, 22, 190);
        }
        .bar:nth-child(3)::before{
            content: var(--t3);
                width: var(--w3);
            background: violet;
        }
        .bar:nth-child(4)::before{
            content: var(--t4);
                width: var(--w4);
            background: gold;
        }
        .bar:nth-child(5)::before{
            content: var(--t5);
                width: var(--w5);
            background: var(--accent);
        }

        .grafica2{
                display: grid;
                place-items: center;
                position: relative;
        }

        .grafica2 > div{
                width: 150px;
                height: 75px;
                overflow: hidden;
                position: relative;
        }

        .cicle{
                position: absolute;
                width: 100%;
                height: 150px;
                border-radius: 50%;
                border: 20px solid rgb(16, 139, 221);
                border-right-color: rgba(0, 0, 0, .6);
                border-bottom-color: rgba(0, 0, 0, .6);
                top: 0; left: 0;
            animation: rotar 2s ease;
            transform: var(--cr);
        }

        .grafica2 > div::before{
            content: var(--t3);
                position: absolute;
                display: inline-block;
            font-family: var(--dosis);
            color: white;
            inset: 0;
            margin: auto;
            margin-bottom: 0;
                width: 60px;
                height: 30px;
                text-align: center;
                font-weight: bold;
        }

        .grafica3{
                display: grid;
                grid: 106px 53px / 1fr 1fr;
                place-items: center;
                gap: 20px;
        }

        .face{
                width: 80%;
                height: 100%;
                border: 5px solid black;
                border-radius: 50%;
                position: relative;
        }

        .face:nth-child(1){
                grid-area: 1 / 1 / 2 / 3;
                width: 106px;
        }

        .face::before{
                content: "";
                width: 5px;
                height: 5px;
                background: black;
                border-radius: 50%;
                position: absolute;
                top: 20%;
                left: 30%;
                box-shadow: black 30px 0 0;
        }

        .face::after{
                content: "";
                width: 30px;
                height: 30px;
                inset: 0;
                margin: auto;
                margin-top: 33%;
                position: absolute;
                border-radius: 50%;
                border: 5px solid transparent;
                border-right-color: rgba(0, 0, 0);
                border-bottom-color: rgba(0, 0, 0);
                transform: rotate(45deg);
        }

        .face:nth-child(2)::after{
                height: 5px;
                margin-top: 25px;
                background: black;
                border: none;
                border-radius: 0;
                transform: rotate(0);
        }

        .face:last-child::after{
                transform: rotate(225deg);
                width: 14px;
                height: 14px;
                margin-top: 20px;
        }
        .face:not(:first-child)::before{
            box-shadow: black 14px 0 0;
        }
        .face:not(:first-child){
            opacity: .4;
        }
        .face:first-child{
            animation: escalar 1.8s ease infinite;
            border-color: var(--accent);
        }
        .face:first-child::before{
            background: var(--accent);
                box-shadow: var(--accent) 30px 0 0;
        }
        .face:first-child::after{
            border-right-color: var(--accent);
                border-bottom-color: var(--accent);
        }
        
![image](https://user-images.githubusercontent.com/50422794/199077332-89ed69be-1563-42d9-a1ab-eca056455711.png)



---------------.------HTML----------------------- 

* Para la crear la checklist se clonó el repositorio con la estructura base anteriormente descrita.
Se estructuró el html ubicando la sección que seria la checklist, se crea un h1 con la clase "title-checklist" y  <div></div> con la clase "work" que representan cada card que conforma la checklist. también se define el div que da origen al "+" que representa el agregar una nueva tarea.

    <section class="chechlist">
        <div class="work">...</div>
        <div class="work">...</div>
        <div class="work">...</div>
        <div class="add">...</div>
    </section>

* Dentro de los div que conforman cada card de tarea se crearon un input y un label con la clase "label-card" para posteriormente agregarle la funcionalidad del check a cada card con css vanila.

    <input type="checkbox" id="active" checked>
            <label class="label-card" for="active"></label>


* Dentro de los label se añadieron el titulo "h1" y los div que contienen cada elemento de la card con sus clases correspondientes que hicieran mas sensillo aplicar los estilos.

    <label class="label-card" for="active">
                <div class="check"> </div>
                <h1 class="title-work">Territorio y medio ambiente.</h1>
                <div class="container1"><p class="state"><b>Pendiente</b></p></div>
                    <div class="student">
                        <div><p class="student-name"><b>Jacobo Bans</b></p></div>
                        <img class="img-student" src="/src/img/s1.png" alt="">
                    </div>
                    <div class="studing">
                        <p>Ingeniería Ambiental</p>
                        <p class="activity"><b>Proyecto de grado</b></p>
                    </div>
                    <div class="container"></div>
                    <div>
                        <p class="calification-1"><b>Calificación</b></p>
                        <div class="calification">
                            <div class="star"></div>
                            <div class="star"></div>
                            <div class="star"></div>
                            <div class="star"></div>
                            <div class="star"></div>
                        </div>
                    </div>
            </label>

--------------------CSS----------------------

* Se define el tamaño del titulo de la sección y los estilos.

        .title-checklist{
        font-size: clamp(1.3rem, 2.5vw, 3rem);
        padding: 20px ;
        text-align: center;
        color: black;
        }
* Así mismo se definen los estilos en cada sección, donde no se presentaron mayores inconvenientes.

   - En el label se utilizó grid para ordenar los elementos dentro de este y que quedaran como los mockups presentados. A las columnasa se les asignaron sus tamaños en porcentajes.

            .label-card{
                display: grid;
                grid-template-columns: 50% 15% 35%;
            }
* El label tiene dentro unas estrellas con las que se hará referencia a la calificación del estudiante, ya que no se pueden usar íconos estas estrellas se elaboraron utilizando la propiedad, clip-path de la siguiente forma.

    .star, .star:before{
    position: relative;
    width: 40px;
    height: 40px;
    background-color: #e9a8a8;
    clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
    }

* Para hacer la sección del check en la label-card se oculta el checkbox para posteriormente crear un pseudoelemento  en label-card al cual se puede agregar y manipular los estilos.

    [type="checkbox"]{
        display:none;
    }

    .label-card:before{
    content:'';
    border: solid 1.5px #e9a8a8;
    border-radius: 3px;
    width: 20px;
    height: 20px;
    position: absolute;
    left: 20px;
    top: 20px;
    transition: all 0.2s;
    transform: rotate(0deg);
    margin-top: 5px;
    }

* Le indicamos al navegador que cuando el checkbox este :checked el label hara dicha acción en este caso cambia el backgroun a verde oscuro las letras a color blanco y el numero de la calificación se hace 5 de 5 indicando que aprobó el estudiante.

    [type="checkbox"]:checked + .label-card{
        color: #fff;
        content: '';
        background-color: var(--dark);
        border:var(--dark) solid 2px;
        --t:"5/5"
    }

* También indicamos que cuando  el input esté en :Checked el label:before sufra cambios, estos seran que el borde se vuelva blanco y que tenga una animación que haga rotar este pseudoelemento 360°.

        [type="checkbox"]:checked + .label-card:before{
        border-color: #fff;
        color: var(--dark);
        content:'';
        transform: rotate(360deg);
        background-color: #fff;
        }

* Necesitaba crear el check, la palomita que va dentro del pseudoelemento, que reflejara que la tarea estuviese hecha. No se puede utilizar iconos por lo que se crea un div con la clase check dentro del label al cual se le dió alto y ancho, se elimina el borde izquierdo y el superior por lo que queda una L invertida a la cual solo con un rotación de 40deg se logra obtener la figura esperada.

        .check{
        display: none;
        position: absolute;
        margin: auto;
        top:25px;
        left:27px;
        width: 10px;
        height: 20px;
        border: var(--accent) 3px solid;
        border-left: none;
        border-top: none;
        transform: rotate(40deg);
        z-index: 10;
        }

* Entonces ya se tiene este elemento de check pero no se observa en el estado inicial de la card, pero como se hizo para que funcionara al check del input,  pues se colocan los estados del elemento dependiendo si está o no seleccionado, es decir, si la card está seleccionada el check debe aparecer. Esto se logra de la siguiente forma 

        [type="checkbox"]:checked + .label-card .check{
            display: block;
        }

* Del mismo modo, al seleccionarse la card, las estrellas deben cambiar de blanco a amarillo y la palabra pendiente debe desaparecer.

        [type="checkbox"]:checked + .label-card .state{
        display: none;
        }
        [type="checkbox"]:checked + .label-card .star:before{
            background-color: yellow;
        }

* Para lograr el efecto de cambio en los numeros de calificación que refleja la card, pasa de el estado 0/5 a 5/5 al ser seleccionado el label, se utilizaron variables para que se hiciera el cambio de numeros al ser chequeada la card.
    - Se define la variable --t="0/5" en :root

            :root{
                --t:"0/5"
            }

    - Se coloca al elemento calification un :before  cuyo contenido es la variable asignada inicialmentey se le dan los estilos correspondientes.

            .calification::before{
                content: var(--t);
                position: absolute;
                top:0;
                right: 110%;
                font-size: 1.3rem;
                height: 100%;
                line-height: 50px;
                display: block;
                font-family: var(--dosis);
                font-weight: bold;
            }

    - Posteriormente se le dice a este pseudoelemento que cuando este chequeada o seleccionada la card que lo contiene su variable debe cambiar su valor a --t="5/5"

                [type="checkbox"]:checked + .label-card{
                color: #fff;
                content: '';
                background-color: var(--dark);
                border:var(--dark) solid 2px;
                --t:"5/5"
            }

* Al tener la funcionalidad de las car correctamente se comienza a aplicar el responsive design utilizando mediaquerys. 

            @media (max-width: 1000px) and (min-width: 481px)
            @media (max-width:380px).

* Por ultimo se añaden animaciones al elemento Add que es el "+" que representa agregar tarea dandole una animación utilizando Keyframes especificados en porcentajes.

            @keyframes palpitar {
            0%{
                transform: scale(1)
            }
            50%{
                transform: scale(1.2)
            }
            100%{
                transform: scale(1)
            }
        }
