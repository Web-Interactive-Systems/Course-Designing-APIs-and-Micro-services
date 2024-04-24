---
type: NoteCard
tags: []
---

# Understand MVC for Web APIs

In this unit we will learn about the Model-View-Controller (MVC) pattern. MVC is a design pattern commonly used in software development, including web development, to separate concerns and organize code into small, well defined, components. In the context of NodeJS, the MVC pattern is often used in frameworks like ExpressJS to build scalable and maintainable APIs.

![](attachments/node-mvc.png)

### Model

The model represents the application's data. It interacts with the database or any other data source to perform CRUD (Create, Read, Update, Delete) operations and encapsulates the logic for manipulating data. In Node.js, models are typically implemented using Object-Relational Mapping (ORM) libraries like Mongoose for MongoDB or Sequelize for SQL databases.

## View

The view is responsible for rendering the user interface and presenting data to the user. It receives data from the controller and generates HTML, JSON, or other types of responses to be sent to the client. In Node.js, views are often implemented using template engines like EJS, Handlebars, or Pug, which allow developers to generate dynamic HTML content by embedding data and logic into templates.

## Controller

The controller acts as an intermediary between the model and the view. It receives input from the client, invokes the appropriate methods on the model to perform the necessary operations, and passes the resulting data to the view for rendering. Controllers handle incoming HTTP requests, route them to the appropriate actions, and orchestrate the flow of data within the application. In Node.js, controllers are implemented as middleware functions in Express.js routes.

## Example of Poeple API Using MVC

In this example the view is a JSON data that is returned to the client. Modern approaches use JSON to exchange data between client and server.

**Database**

```js
// db.js
const people = [
  { id: 1, name: 'john' },
  { id: 2, name: 'peter' },
  { id: 3, name: 'susan' },
  { id: 4, name: 'anna' },
  { id: 5, name: 'emma' },
]
module.exports = { people }
```

**Models**

```js
// model.js
import { people } from './db.js';

export const getById = (id) => {
  return people.find(id => id === id);
}

export const create = (data) => {

  data.id = Math.random(); 
  people.push(data);

  return data;
}

// ...
```

**Controllers**

```js
// controller.js

import { findById, create } from './model.js';

const getPeopleById = (req, res) => {
  const { id } = req.body;

  const people = getById(id);

  res.status(200).json({ success: true, data: people })
}

const createPeople = (req, res) => {
  const { name } = req.body;

  const people =  create({ name });

  res.status(200).json({ success: true, data: people })
}

// ...
```

**Routes**

```js
// routes
import express from 'express';

import { getPeopleById, createPeople } from './controller.js';

const router = express.Router()

router.route('/:id').get(getPeopleById)
router.route('/create').post(createPeople)


module.exports = router
```

**Server**

```js
// server.js
import express from 'express';

import peopleApi from './routes.js';

const app = express();

// parse form data
app.use(express.urlencoded({ extended: false }));
// parse json
app.use(express.json());

app.use('/api/people', peopleApi);

app.listen(5000, () => {
  console.log('Server is listening on port 5000....')
})
```

## Excalidraws

:::excalidraw
[{"type":"rectangle","version":178,"versionNonce":160715893,"isDeleted":false,"id":"5GpIJCSslvT9pVJhnO8v9","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":169.83050847457628,"y":271.0225105932204,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","width":117,"height":60,"seed":1974453450,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"type":"text","id":"Amm8YmCdLGJbOyvEsRaS9"},{"id":"08DnfHqXEX6cHgNb92Ib2","type":"arrow"},{"id":"g35KSfmwTfj9WcC6hMvAe","type":"arrow"}],"updated":1713863272210,"link":null,"locked":false},{"type":"text","version":142,"versionNonce":1205934427,"isDeleted":false,"id":"Amm8YmCdLGJbOyvEsRaS9","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":175.73050618575792,"y":288.5225105932204,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":105.20000457763672,"height":25,"seed":998465226,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"Controllers","textAlign":"center","verticalAlign":"middle","containerId":"5GpIJCSslvT9pVJhnO8v9","originalText":"Controllers","lineHeight":1.25,"baseline":18},{"type":"rectangle","version":124,"versionNonce":1968963029,"isDeleted":false,"id":"jYiEZOEv_Ij80Ye3DF0gI","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":173.83050847457628,"y":136.2936970338983,"strokeColor":"#1e1e1e","backgroundColor":"#b2f2bb","width":121,"height":58,"seed":1674885974,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"type":"text","id":"SlEmqdfTrW67gyh2htYJQ"},{"id":"08DnfHqXEX6cHgNb92Ib2","type":"arrow"}],"updated":1713863272210,"link":null,"locked":false},{"type":"text","version":95,"versionNonce":483079675,"isDeleted":false,"id":"SlEmqdfTrW67gyh2htYJQ","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":199.78050923751573,"y":152.7936970338983,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":69.0999984741211,"height":25,"seed":1455614678,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"Routes","textAlign":"center","verticalAlign":"middle","containerId":"jYiEZOEv_Ij80Ye3DF0gI","originalText":"Routes","lineHeight":1.25,"baseline":18},{"type":"rectangle","version":176,"versionNonce":1361541941,"isDeleted":false,"id":"42S8nt3pNlg1POSH1mc0-","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":167.4406779661016,"y":402.0564088983051,"strokeColor":"#1e1e1e","backgroundColor":"#ffec99","width":120,"height":54,"seed":61400522,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"type":"text","id":"E6HJr93fUq73LUreGm-5Y"},{"id":"g35KSfmwTfj9WcC6hMvAe","type":"arrow"}],"updated":1713863272210,"link":null,"locked":false},{"type":"text","version":159,"versionNonce":1401470619,"isDeleted":false,"id":"E6HJr93fUq73LUreGm-5Y","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":203.09067758463186,"y":416.5564088983051,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":48.70000076293945,"height":25,"seed":211284246,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"Views","textAlign":"center","verticalAlign":"middle","containerId":"42S8nt3pNlg1POSH1mc0-","originalText":"Views","lineHeight":1.25,"baseline":18},{"type":"text","version":4,"versionNonce":358370453,"isDeleted":true,"id":"al4v79CqCKKGFVgK1eBs9","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":194,"y":269.234375,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":10,"height":25,"seed":220852938,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"","textAlign":"center","verticalAlign":"middle","containerId":"42S8nt3pNlg1POSH1mc0-","originalText":"","lineHeight":1.25,"baseline":18},{"type":"text","version":4,"versionNonce":919352123,"isDeleted":true,"id":"fDW4kFzG85XBjAwiEccZv","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":35,"y":93.734375,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":10,"height":25,"seed":978199434,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"","lineHeight":1.25,"baseline":18},{"type":"text","version":40,"versionNonce":296743413,"isDeleted":false,"id":"FLuR9JK5FTd7wOMD0Yw9B","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":20,"y":94.734375,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":97.13999938964844,"height":50,"seed":589500042,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"HTTP\nREQUEST","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"HTTP\nREQUEST","lineHeight":1.25,"baseline":43},{"type":"text","version":52,"versionNonce":385356763,"isDeleted":false,"id":"uW4Ve40QX9K1gAR7KF-v4","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":5.785714285714391,"y":231.091517857143,"strokeColor":"#1e1e1e","backgroundColor":"#ffec99","width":105.45999145507812,"height":50,"seed":168462730,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"HTTP\nRESPONSE","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"HTTP\nRESPONSE","lineHeight":1.25,"baseline":43},{"type":"text","version":4,"versionNonce":52947797,"isDeleted":true,"id":"vRcN9pAfqDwN1KTo3FGRT","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":100.42857142856951,"y":93.59151785714303,"strokeColor":"#1e1e1e","backgroundColor":"#ffec99","width":10,"height":25,"seed":1791211286,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"","lineHeight":1.25,"baseline":18},{"type":"arrow","version":132,"versionNonce":337567867,"isDeleted":false,"id":"c7zVNiOee0RVoI5BK7M9q","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":11.142857142855064,"y":168.59151785714303,"strokeColor":"#1e1e1e","backgroundColor":"#ffec99","width":110.01815980629533,"height":1.5133171912833063,"seed":1108330198,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[110.01815980629533,1.5133171912833063]]},{"type":"arrow","version":174,"versionNonce":1780070581,"isDeleted":false,"id":"A0mbOT0BzoJay_AftEXsk","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":124.11016949152508,"y":303.7852224576274,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":106.77966101694932,"height":0,"seed":254374794,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863272210,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[-106.77966101694932,0]]},{"type":"rectangle","version":157,"versionNonce":671291675,"isDeleted":false,"id":"irFXC5NWsdkUmgydM9Wg7","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":445.62953995157363,"y":264.8929706416466,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","width":127.11864406779671,"height":54.237288135593275,"seed":926983242,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"type":"text","id":"gXn0ZWIe-31RtGfpnCnH5"},{"id":"zwXeDDqVyU_83Q1ICT-rX","type":"arrow"}],"updated":1713863272210,"link":null,"locked":false},{"type":"text","version":55,"versionNonce":539679253,"isDeleted":false,"id":"gXn0ZWIe-31RtGfpnCnH5","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":476.7688638165266,"y":279.5116147094432,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":64.83999633789062,"height":25,"seed":119473238,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863272211,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"Models","textAlign":"center","verticalAlign":"middle","containerId":"irFXC5NWsdkUmgydM9Wg7","originalText":"Models","lineHeight":1.25,"baseline":18},{"type":"arrow","version":121,"versionNonce":1880571323,"isDeleted":false,"id":"zwXeDDqVyU_83Q1ICT-rX","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":325.80508474576254,"y":295.31064618644086,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":105.29661016949177,"height":3.4806295399515648,"seed":1209823178,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863272211,"link":null,"locked":false,"startBinding":null,"endBinding":{"elementId":"irFXC5NWsdkUmgydM9Wg7","focus":0.09455310472792194,"gap":14.52784503631932},"lastCommittedPoint":null,"startArrowhead":"arrow","endArrowhead":"arrow","points":[[0,0],[105.29661016949177,-3.4806295399515648]]},{"type":"arrow","version":201,"versionNonce":1271147637,"isDeleted":false,"id":"vQstNz5-DhkkvXt6UuzSw","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":595.4313401368047,"y":291.60287852218823,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":128.5108958837775,"height":0,"seed":1598578070,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863276850,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":"arrow","endArrowhead":"arrow","points":[[0,0],[128.5108958837775,0]]},{"type":"ellipse","version":108,"versionNonce":1265185845,"isDeleted":false,"id":"l4d8P1loz8I51LFKIG5rW","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":755.5871670702179,"y":222.52008928571445,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":86.4406779661017,"height":42.372881355932236,"seed":76836426,"groupIds":["MJYNcrEUnkkJ_ZjvV2zhM"],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863279618,"link":null,"locked":false},{"type":"ellipse","version":153,"versionNonce":822011285,"isDeleted":false,"id":"pwthAdB8k3ivjneTjK9Cy","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":762.3668280871673,"y":300.4861909806298,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":86.4406779661017,"height":47.4576271186441,"seed":903309258,"groupIds":["MJYNcrEUnkkJ_ZjvV2zhM"],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863279618,"link":null,"locked":false},{"type":"line","version":74,"versionNonce":798452469,"isDeleted":false,"id":"OcF-eT6ofoU1xKhfnqrT3","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":755.5871670702179,"y":246.24890284503653,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":5.084745762711918,"height":86.4406779661017,"seed":1185776906,"groupIds":["MJYNcrEUnkkJ_ZjvV2zhM"],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863279618,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":null,"points":[[0,0],[5.084745762711918,86.4406779661017]]},{"type":"line","version":76,"versionNonce":1203258453,"isDeleted":false,"id":"ooykdF4xrYRbifrt4ENxr","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":840.3329297820826,"y":244.55398759079924,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":8.474576271186152,"height":66.10169491525426,"seed":1358019734,"groupIds":["MJYNcrEUnkkJ_ZjvV2zhM"],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863279618,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":null,"points":[[0,0],[8.474576271186152,66.10169491525426]]},{"type":"text","version":77,"versionNonce":138895003,"isDeleted":false,"id":"YPQsy42Eq-yauzgz93DMA","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":764.6973365617434,"y":362.3808641041165,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":98.8800048828125,"height":25,"seed":1227288010,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1713863283108,"link":null,"locked":false,"fontSize":20,"fontFamily":1,"text":"Database","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"Database","lineHeight":1.25,"baseline":18},{"type":"arrow","version":27,"versionNonce":377923477,"isDeleted":false,"id":"08DnfHqXEX6cHgNb92Ib2","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":225.80508474576237,"y":208.86996822033916,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","width":0,"height":52.54237288135596,"seed":623043402,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863272211,"link":null,"locked":false,"startBinding":{"elementId":"jYiEZOEv_Ij80Ye3DF0gI","focus":0.14091609469113894,"gap":14.576271186440863},"endBinding":{"elementId":"5GpIJCSslvT9pVJhnO8v9","focus":-0.04316963638998128,"gap":9.610169491525255},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[0,52.54237288135596]]},{"type":"arrow","version":26,"versionNonce":2018052155,"isDeleted":false,"id":"g35KSfmwTfj9WcC6hMvAe","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":220.72033898305045,"y":395.310646186441,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","width":0,"height":50.84745762711873,"seed":615520010,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1713863272211,"link":null,"locked":false,"startBinding":{"elementId":"42S8nt3pNlg1POSH1mc0-","focus":-0.11200564971751893,"gap":6.745762711864131},"endBinding":{"elementId":"5GpIJCSslvT9pVJhnO8v9","focus":0.13008836737650978,"gap":13.440677966101873},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[0,-50.84745762711873]]}]
:::

