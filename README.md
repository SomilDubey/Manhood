import React, { useState } from "react"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card"; import { ShoppingBag, Shirt, Search } from "lucide-react";

const products = [ { id: 1, name: "Classic T-Shirt", price: 20, image: "https://via.placeholder.com/200x200?text=T-Shirt" }, { id: 2, name: "Denim Jacket", price: 45, image: "https://via.placeholder.com/200x200?text=Jacket" }, { id: 3, name: "Casual Shirt", price: 30, image: "https://via.placeholder.com/200x200?text=Shirt" }, { id: 4, name: "Summer Dress", price: 35, image: "https://via.placeholder.com/200x200?text=Dress" }, ];

export default function ClothingStore() { const [cart, setCart] = useState([]);

const addToCart = (product) => { setCart([...cart, product]); };

const getTotal = () => { return cart.reduce((total, item) => total + item.price, 0); };

const checkout = () => { alert(Checkout successful! Total: $${getTotal()}); setCart([]); };

return ( <div className="min-h-screen bg-white p-6"> <header className="flex justify-between items-center py-4 border-b mb-6"> <div className="flex items-center space-x-2 text-xl font-bold"> <Shirt /> <span>ManHood</span> </div> <div className="flex items-center space-x-2"> <input
type="text"
placeholder="Search clothes..."
className="border rounded px-2 py-1"
/> <Button variant="outline"> <Search size={16} /> </Button> </div> <div className="flex items-center gap-2"> <ShoppingBag size={16} /> <span>{cart.length} items</span> <Button onClick={checkout} variant="default"> Checkout (${getTotal()}) </Button> </div> </header>

<main>
    <h2 className="text-2xl font-semibold mb-4">Latest Collection</h2>
    <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
      {products.map((product) => (
        <Card key={product.id} className="hover:shadow-lg transition">
          <CardContent className="p-2">
            <img src={product.image} alt={product.name} className="w-full rounded-xl mb-2" />
            <div className="text-lg font-medium">{product.name}</div>
            <div className="text-sm text-gray-500">${product.price}</div>
            <Button className="mt-2 w-full" onClick={() => addToCart(product)}>
              Add to Cart
            </Button>
          </CardContent>
        </Card>
      ))}
    </div>
  </main>

  <footer className="text-center mt-10 text-sm text-gray-500">
    © 2025 ManHood. All rights reserved.
  </footer>
</div>

); }

