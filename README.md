Introducción:
==============
FireFiles es una API (enfocada generalmente en Discord) generadora de imágenes aleatorias, que busca facilitar la creación de comandos de interacción en la comunidad de programadores.

Endpoints:
==============
|  Nombre  |        Descripción           |
|----------|:----------------------------:|
| smoke    | Vamos, puedes fumar un poco. |
| hug      | Abraza a los que mas quieres.|

Obtener Link:
==============
Base simple para obtener el link, dependiendo del nombre del endpoint que deseas:

> https://firefiles.herokuapp.com/[nombre_endpoint]

Ejemplos:
==============
A continuación, unos ejemplos de como utilizar el API. En este primero nos ayudaremos del módulo `superagent`, también teniendo en cuenta a `discord.js`:

**Instalación del módulo superagent:**

```js
$ npm i superagent
```

**Código ejemplo:**

```js
 const Discord = require("discord.js");
 const superagent = require("superagent"); // Utilizamos el módulo para obtener las imágenes.
 let { body } = await superagent.get("https://firefiles.herokuapp.com/smoke")// Con el modulo obtiene los resultados de la página, en este caso el endpoint será "smoke".
 let link = body.url //Obtenemos el link de la imágen generada.
    const embed = new Discord.RichEmbed() //Preferible crear un embed, ya que la imágen se devuelve como una URL.
      .setDescription(message.author+" ha empezado a fumar.")
      .setColor("RANDOM")
      .setImage(link)
      .setFooter("Powered by: FireFiles") //Se agradecería mucho si dieran creditos a la api. :)
    message.channel.send(embed) //Enviamos el mensaje embed al canal.
```

En este otro ejemplo, nos ayudaremos del módulo `got`, también teniendo en cuenta a `discord.js`:

**Instalación del módulo got:**

```js
$ npm i got
```
**Código ejemplo:**

```js
  const got = require('got'); //Utilizamos otro módulo, que hace la misma función que el anterior.
  got('https://firefiles.herokuapp.com/hug').then(res => { //Obtiene los resultados de la página, en este caso el endpoint será "hug" y luego hace lo siguiente:
    
  message.channel.send(JSON.parse(res.body).url); //Enviamos el URL al canal.
    /*
        NOTA:
        Tambien puede usar message.channel.send({files: [JSON.parse(res.body).url)]}); para mostrar la imágen sin link, o crear un embed.
    */
});
```

Enlaces:
==============
Tenemos un servidor de Discord, en el que ofrecemos soporte, hay mas codes de ejemplos, puedes aportar tus ideas, se notificarán de nuevos endpoints y muchas cosas más! [[Click Aquí.]](https://discord.gg/6DJxrSZ)
