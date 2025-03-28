import { useState } from "react";
import { Button } from "@/components/ui/button";


export default function Cetenry() {
  const [cart, setCart] = useState([]);


  const products = [
    { id: 1, name: "T-Shirt Logo", price: 25, image: "/tshirt.jpg" },
    { id: 2, name: "Hoodie Premium", price: 50, image: "/hoodie.jpg" },
    { id: 3, name: "Casquette", price: 20, image: "/cap.jpg" }
  ];


  const addToCart = (product) => {
    setCart([...cart, product]);
  };


  return (
    <div className="p-6 bg-gray-100 min-h-screen">
      <header className="text-center mb-6">
        <h1 className="text-4xl font-bold">Cetenry - Marque de Vêtements</h1>
      </header>
      
      <main className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {products.map((product) => (
          <div key={product.id} className="border p-4 rounded-lg shadow-lg bg-white">
            <img src={product.image} alt={product.name} className="w-full h-40 object-cover mb-4" />
            <h2 className="text-xl font-semibold">{product.name}</h2>
            <p className="text-gray-700">{product.price}€</p>
            <Button className="mt-2" onClick={() => addToCart(product)}>Ajouter au panier</Button>
          </div>
        ))}
      </main>
      
      <aside className="mt-6 p-4 bg-white shadow-lg rounded-lg">
        <h2 className="text-xl font-semibold">Panier</h2>
        {cart.length === 0 ? (
          <p className="text-gray-500">Votre panier est vide.</p>
        ) : (
          <ul>
            {cart.map((item, index) => (
              <li key={index} className="border-b py-2">{item.name} - {item.price}€</li>
            ))}
          </ul>
        )}
      </aside>
    </div>
  );
}


