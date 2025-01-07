# React Router Dom
```
npm install react-router-dom
```
- src/App.jsx
```
import { createBrowserRouter, Outlet, RouterProvider } from "react-router-dom"
import Home from "./Home"
import Aboutus from "./Aboutus"
import Contact from "./Contact"
import Navbar from "./Navbar"
import Footer from "./Footer"
import Dashboard from "./Dashboard"
import Health from "./Health"
import Food from "./Food"
import Category from "./Category"


const App = () => {

const router = createBrowserRouter([
  { path: "/", element: (<>
  <Navbar/>
  <Outlet/>
  <Footer/>
  </>),
    children: [
      { path: "/", element: <Home/>},
      { path: "aboutus", element: <Aboutus/>},
      ]
   },
   { path: "/", element:(<>
   <Navbar/>
   <Outlet/>
   </>) ,
    children: [
      {path: "contact", element: <Contact/>},
      { path: "contact/food", element: <Food/>},
      { path: "contact/health", element: <Health/>},
    ]
  },
   {path: "category/:id", element: <Category/>},
   { path: "*", element: <h1>Page not found</h1>},
 ])

  return (
    <>
       <RouterProvider router={router}/>
    </>
  )
}

export default App
```
- src/Navbar.jsx
```
import { Link } from "react-router-dom"

const Navbar = () => {
  return (
    <>
       <ul>
<div>
  <li><Link to="/">Home</Link></li>
  <li><Link to="aboutus">About</Link></li>
  <li><Link to="contact">Contact</Link></li>
  <li><Link to="dashboard">Dashboard</Link></li>
</div>

       </ul>
    </>
  )
}

export default Navbar
```
- src/footer.jsx
```
const Footer = () => {
  return (
    <>
        <h2>This is a Footer</h2>
    </>
  )
}

export default Footer
```
- src/home.jsx
```
const Home = () => {
  return (
    <>
        <h1>Welcome to the Home Page</h1>
    </>
  )
}

export default Home
```
- src/aboutus.jsx
```
import { useNavigate } from "react-router-dom"


const Aboutus = () => {
    const navigate = useNavigate()



  return (
    <>
    <>Aboutus</>
<button onClick={()=>navigate('/category/abcd')}>Route Parameter</button>
</>
  )
}

export default Aboutus
```
- src/contact.jsx
```
import { useNavigate } from "react-router-dom"

const Contact = () => {
    const navigate = useNavigate()


  return (
    <>
    <>Contact</>
    <button onClick={()=>navigate('food')}>Food</button>
    <button onClick={()=>navigate('health')}>Health</button>
    </>
  )
}

export default Contact
```
- src/health.jsx
```
const Health = () => {
  return (
    <div>Health</div>
  )
}

export default Health
```
- src/food.jsx
```
const Food = () => {
  return (
    <div>Food</div>
  )
}

export default Food
```
- src/category.jsx
```
import { useParams } from "react-router-dom"

const Category = () => {
     const {id} = useParams()


  return (
    <div>My Category id is: {id}</div>

  )
}

export default Category
```
