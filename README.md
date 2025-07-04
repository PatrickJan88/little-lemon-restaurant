# little-lemon-restaurant
// **peer review**

import React, { useState } from 'react';
import { Calendar, Clock, Users, Star, ChefHat, Phone, MapPin, Mail } from 'lucide-react';

const LittleLemonRestaurant = () => {
  const [bookingForm, setBookingForm] = useState({
    date: '',
    time: '',
    guests: '2',
    name: '',
    email: '',
    phone: ''
  });

  const [activeSection, setActiveSection] = useState('home');

  const handleInputChange = (e) => {
    setBookingForm({
      ...bookingForm,
      [e.target.name]: e.target.value
    });
  };

  const handleBooking = () => {
    if (!bookingForm.date || !bookingForm.time || !bookingForm.name || !bookingForm.email || !bookingForm.phone) {
      alert('Please fill in all required fields');
      return;
    }
    alert(`Reservation confirmed for ${bookingForm.name} on ${bookingForm.date} at ${bookingForm.time} for ${bookingForm.guests} guests!`);
    setBookingForm({
      date: '',
      time: '',
      guests: '2',
      name: '',
      email: '',
      phone: ''
    });
  };

  const recommendedDishes = [
    {
      name: 'Grilled Salmon',
      description: 'Fresh Atlantic salmon with lemon herb crust and seasonal vegetables',
      price: '$28.99',
      image: 'https://images.pexels.com/photos/1516415/pexels-photo-1516415.jpeg',
      rating: 4.9,
      emoji: '🐟'
    },
    {
      name: 'Mediterranean Burrito',
      description: 'Fusion wrap with hummus, grilled chicken, olives, and tzatziki',
      price: '$16.99',
      image: 'https://images.pexels.com/photos/2474658/pexels-photo-2474658.jpeg',
      rating: 4.7,
      emoji: '🌯'
    },
    {
      name: 'Truffle Pizza',
      description: 'Wood-fired pizza with truffle oil, wild mushrooms, and arugula',
      price: '$22.99',
      image: 'https://images.pexels.com/photos/315755/pexels-photo-315755.jpeg',
      rating: 4.8,
      emoji: '🍕'
    },
    {
      name: 'Bistro Steak',
      description: 'Premium cut with roasted garlic butter and herb potatoes',
      price: '$34.99',
      image: 'https://images.pexels.com/photos/769289/pexels-photo-769289.jpeg',
      rating: 4.9,
      emoji: '🥩'
    }
  ];

  const fusionDishes = [
    {
      name: 'Korean BBQ Tacos',
      description: 'Marinated bulgogi beef with kimchi slaw and gochujang aioli',
      price: '$18.99',
      image: 'https://images.pexels.com/photos/4958792/pexels-photo-4958792.jpeg',
      emoji: '🌮'
    },
    {
      name: 'Thai Curry Risotto',
      description: 'Creamy arborio rice with red curry, coconut milk, and prawns',
      price: '$24.99',
      image: 'https://images.pexels.com/photos/5926382/pexels-photo-5926382.jpeg',
      emoji: '🍛'
    },
    {
      name: 'Sushi Burger',
      description: 'Crispy rice patty with sashimi-grade tuna and wasabi mayo',
      price: '$19.99',
      image: 'https://images.pexels.com/photos/1640777/pexels-photo-1640777.jpeg',
      emoji: '🍔'
    },
    {
      name: 'Indian Spiced Lamb Pizza',
      description: 'Naan base with tandoori lamb, mint chutney, and fresh cilantro',
      price: '$26.99',
      image: 'https://images.pexels.com/photos/1566837/pexels-photo-1566837.jpeg',
      emoji: '🍕'
    }
  ];

  const menuCategories = [
    {
      category: 'Appetizers',
      items: [
        { name: 'Lemon Bruschetta', price: '$12.99', description: 'Toasted bread with tomatoes, basil, and lemon zest' },
        { name: 'Calamari Rings', price: '$14.99', description: 'Crispy squid with marinara sauce' },
        { name: 'Cheese Board', price: '$18.99', description: 'Selection of artisanal cheeses with crackers' }
      ]
    },
    {
      category: 'Main Courses',
      items: [
        { name: 'Lemon Chicken', price: '$25.99', description: 'Herb-crusted chicken with lemon butter sauce' },
        { name: 'Seafood Pasta', price: '$29.99', description: 'Linguine with mixed seafood in white wine sauce' },
        { name: 'Ribeye Steak', price: '$39.99', description: 'Premium cut with garlic mashed potatoes' }
      ]
    },
    {
      category: 'Desserts',
      items: [
        { name: 'Lemon Tart', price: '$8.99', description: 'Classic tart with fresh berries' },
        { name: 'Tiramisu', price: '$9.99', description: 'Traditional Italian dessert' },
        { name: 'Chocolate Lava Cake', price: '$10.99', description: 'Warm cake with molten chocolate center' }
      ]
    }
  ];

  const Navigation = () => (
    <nav className="bg-white shadow-md sticky top-0 z-50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex justify-between items-center h-16">
          <div className="flex items-center">
            <span className="text-2xl font-bold text-yellow-600">🍋 Little Lemon</span>
          </div>
          <div className="flex space-x-8">
            {['Home', 'Menu', 'Reservations', 'About', 'Contact'].map((item) => (
              <button
                key={item}
                onClick={() => setActiveSection(item.toLowerCase())}
                className={`px-3 py-2 rounded-md text-sm font-medium transition-colors ${
                  activeSection === item.toLowerCase()
                    ? 'text-yellow-600 bg-yellow-50'
                    : 'text-gray-700 hover:text-yellow-600'
                }`}
              >
                {item}
              </button>
            ))}
          </div>
        </div>
      </div>
    </nav>
  );

  const HeroSection = () => (
    <section className="bg-gradient-to-r from-yellow-400 via-yellow-500 to-orange-400 text-white py-20">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center">
          <h1 className="text-5xl font-bold mb-6">Welcome to Little Lemon</h1>
          <p className="text-xl mb-8 max-w-2xl mx-auto">
            Experience the perfect fusion of Mediterranean flavors and modern cuisine 
            in our vibrant bistro atmosphere
          </p>
          <div className="flex flex-col sm:flex-row gap-4 justify-center">
            <button
              onClick={() => setActiveSection('reservations')}
              className="bg-white text-yellow-600 px-8 py-3 rounded-lg font-semibold hover:bg-gray-100 transition-colors"
            >
              Make Reservation
            </button>
            <button
              onClick={() => setActiveSection('menu')}
              className="border-2 border-white text-white px-8 py-3 rounded-lg font-semibold hover:bg-white hover:text-yellow-600 transition-colors"
            >
              View Menu
            </button>
          </div>
        </div>
      </div>
    </section>
  );

  const ReservationSection = () => (
    <section className="py-16 bg-gray-50">
      <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">Make a Reservation</h2>
          <p className="text-lg text-gray-600">Book your table for an unforgettable dining experience</p>
        </div>
        
        <div className="bg-white rounded-lg shadow-lg p-8">
          <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                <Calendar className="inline w-4 h-4 mr-2" />
                Date
              </label>
              <input
                type="date"
                name="date"
                value={bookingForm.date}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              />
            </div>
            
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                <Clock className="inline w-4 h-4 mr-2" />
                Time
              </label>
              <select
                name="time"
                value={bookingForm.time}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              >
                <option value="">Select time</option>
                <option value="17:00">5:00 PM</option>
                <option value="17:30">5:30 PM</option>
                <option value="18:00">6:00 PM</option>
                <option value="18:30">6:30 PM</option>
                <option value="19:00">7:00 PM</option>
                <option value="19:30">7:30 PM</option>
                <option value="20:00">8:00 PM</option>
                <option value="20:30">8:30 PM</option>
                <option value="21:00">9:00 PM</option>
              </select>
            </div>
            
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                <Users className="inline w-4 h-4 mr-2" />
                Number of Guests
              </label>
              <select
                name="guests"
                value={bookingForm.guests}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              >
                {[1,2,3,4,5,6,7,8,9,10].map(num => (
                  <option key={num} value={num}>{num} {num === 1 ? 'guest' : 'guests'}</option>
                ))}
              </select>
            </div>
            
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
              <input
                type="text"
                name="name"
                value={bookingForm.name}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              />
            </div>
            
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">Email</label>
              <input
                type="email"
                name="email"
                value={bookingForm.email}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              />
            </div>
            
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">Phone</label>
              <input
                type="tel"
                name="phone"
                value={bookingForm.phone}
                onChange={handleInputChange}
                className="w-full px-3 py-2 border border-gray-300 rounded-md focus:ring-yellow-500 focus:border-yellow-500"
                required
              />
            </div>
            
            <div className="md:col-span-2">
              <button
                type="button"
                onClick={handleBooking}
                className="w-full bg-yellow-600 text-white py-3 px-6 rounded-md font-semibold hover:bg-yellow-700 transition-colors"
              >
                Confirm Reservation
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  );

  const RecommendedDishes = () => (
    <section className="py-16 bg-white">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">Chef's Recommendations</h2>
          <p className="text-lg text-gray-600">Signature dishes that define our culinary excellence</p>
        </div>
        
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          {recommendedDishes.map((dish, index) => (
            <div key={index} className="bg-white rounded-xl shadow-lg overflow-hidden hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
              <div className="relative h-56 overflow-hidden bg-gradient-to-br from-yellow-50 to-orange-50">
                <img 
                  src={dish.image} 
                  alt={dish.name}
                  className="w-full h-full object-cover hover:scale-110 transition-transform duration-500"
                  onError={(e) => {
                    e.target.style.display = 'none';
                    e.target.nextSibling.style.display = 'flex';
                  }}
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent"></div>
                <div className="hidden absolute inset-0 items-center justify-center bg-gradient-to-br from-yellow-100 to-orange-100">
                  <span className="text-6xl">{dish.emoji}</span>
                </div>
              </div>
              <div className="p-6">
                <div className="flex items-center justify-between mb-2">
                  <h3 className="text-xl font-bold text-gray-900">{dish.name}</h3>
                  <div className="flex items-center bg-yellow-100 px-2 py-1 rounded-full">
                    <Star className="w-4 h-4 text-yellow-500 fill-current" />
                    <span className="ml-1 text-sm font-semibold text-yellow-700">{dish.rating}</span>
                  </div>
                </div>
                <p className="text-gray-600 mb-4 text-sm leading-relaxed">{dish.description}</p>
                <div className="flex items-center justify-between">
                  <div className="text-2xl font-bold text-yellow-600">{dish.price}</div>
                  <button className="bg-yellow-500 hover:bg-yellow-600 text-white px-4 py-2 rounded-lg font-medium transition-colors">
                    Order Now
                  </button>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );

  const FusionDishes = () => (
    <section className="py-16 bg-gray-50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">Fusion Specialties</h2>
          <p className="text-lg text-gray-600">Where global flavors meet culinary innovation</p>
        </div>
        
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          {fusionDishes.map((dish, index) => (
            <div key={index} className="bg-white rounded-xl shadow-lg overflow-hidden hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
              <div className="relative h-56 overflow-hidden bg-gradient-to-br from-orange-50 to-red-50">
                <img 
                  src={dish.image} 
                  alt={dish.name}
                  className="w-full h-full object-cover hover:scale-110 transition-transform duration-500"
                  onError={(e) => {
                    e.target.style.display = 'none';
                    e.target.nextSibling.style.display = 'flex';
                  }}
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent"></div>
                <div className="hidden absolute inset-0 items-center justify-center bg-gradient-to-br from-orange-100 to-red-100">
                  <span className="text-6xl">{dish.emoji}</span>
                </div>
                <div className="absolute top-4 left-4 bg-red-500 text-white px-3 py-1 rounded-full text-sm font-bold">
                  FUSION
                </div>
              </div>
              <div className="p-6">
                <h3 className="text-xl font-bold text-gray-900 mb-2">{dish.name}</h3>
                <p className="text-gray-600 mb-4 text-sm leading-relaxed">{dish.description}</p>
                <div className="flex items-center justify-between">
                  <div className="text-2xl font-bold text-orange-600">{dish.price}</div>
                  <button className="bg-orange-500 hover:bg-orange-600 text-white px-4 py-2 rounded-lg font-medium transition-colors">
                    Try It
                  </button>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );

  const MenuSection = () => (
    <section className="py-16 bg-white">
      <div className="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">Our Menu</h2>
          <p className="text-lg text-gray-600">Fresh ingredients, bold flavors, exceptional presentation</p>
        </div>
        
        <div className="space-y-12">
          {menuCategories.map((category, index) => (
            <div key={index}>
              <h3 className="text-2xl font-bold text-gray-900 mb-6 text-center">{category.category}</h3>
              <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                {category.items.map((item, itemIndex) => (
                  <div key={itemIndex} className="bg-gray-50 rounded-lg p-6 hover:bg-gray-100 transition-colors">
                    <div className="flex justify-between items-start mb-2">
                      <h4 className="text-lg font-semibold text-gray-900">{item.name}</h4>
                      <span className="text-lg font-bold text-yellow-600">{item.price}</span>
                    </div>
                    <p className="text-gray-600">{item.description}</p>
                  </div>
                ))}
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );

  const AboutSection = () => (
    <section className="py-16 bg-gray-50">
      <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">About Little Lemon</h2>
        </div>
        
        <div className="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
          <div>
            <h3 className="text-2xl font-semibold mb-4">Our Story</h3>
            <p className="text-gray-600 mb-4">
              Little Lemon was born from a passion for bringing together the vibrant flavors 
              of the Mediterranean with innovative culinary techniques. Our bistro atmosphere 
              creates the perfect setting for memorable dining experiences.
            </p>
            <p className="text-gray-600 mb-4">
              From our signature salmon dishes to our creative fusion cuisine, every plate 
              tells a story of culinary excellence and attention to detail.
            </p>
            <div className="flex items-center">
              <ChefHat className="w-6 h-6 text-yellow-600 mr-2" />
              <span className="text-gray-700">Chef-driven cuisine since 2020</span>
            </div>
          </div>
          <div className="bg-white rounded-lg p-8 shadow-md">
            <h3 className="text-xl font-semibold mb-4">Why Choose Little Lemon?</h3>
            <ul className="space-y-3 text-gray-600">
              <li>• Fresh, locally-sourced ingredients</li>
              <li>• Innovative fusion cuisine</li>
              <li>• Warm, welcoming bistro atmosphere</li>
              <li>• Expert culinary team</li>
              <li>• Extensive wine selection</li>
              <li>• Perfect for any occasion</li>
            </ul>
          </div>
        </div>
      </div>
    </section>
  );

  const ContactSection = () => (
    <section className="py-16 bg-white">
      <div className="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center mb-12">
          <h2 className="text-3xl font-bold text-gray-900 mb-4">Contact Us</h2>
          <p className="text-lg text-gray-600">We'd love to hear from you</p>
        </div>
        
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div className="text-center">
            <MapPin className="w-8 h-8 text-yellow-600 mx-auto mb-4" />
            <h3 className="text-xl font-semibold mb-2">Location</h3>
            <p className="text-gray-600">123 Mediterranean Ave<br />Chicago, IL 60601</p>
          </div>
          <div className="text-center">
            <Phone className="w-8 h-8 text-yellow-600 mx-auto mb-4" />
            <h3 className="text-xl font-semibold mb-2">Phone</h3>
            <p className="text-gray-600">(555) 123-LEMON<br />(555) 123-5366</p>
          </div>
          <div className="text-center">
            <Mail className="w-8 h-8 text-yellow-600 mx-auto mb-4" />
            <h3 className="text-xl font-semibold mb-2">Email</h3>
            <p className="text-gray-600">info@littlelemon.com<br />reservations@littlelemon.com</p>
          </div>
        </div>
      </div>
    </section>
  );

  const Footer = () => (
    <footer className="bg-gray-900 text-white py-8">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="text-center">
          <div className="text-2xl font-bold text-yellow-400 mb-4">🍋 Little Lemon</div>
          <p className="text-gray-400 mb-4">Where Mediterranean meets modern cuisine</p>
          <div className="flex justify-center space-x-6">
            <span className="text-gray-400">Mon-Thu: 5:00 PM - 10:00 PM</span>
            <span className="text-gray-400">Fri-Sat: 5:00 PM - 11:00 PM</span>
            <span className="text-gray-400">Sun: 5:00 PM - 9:00 PM</span>
          </div>
        </div>
      </div>
    </footer>
  );

  return (
    <div className="min-h-screen bg-gray-50">
      <Navigation />
      
      {activeSection === 'home' && (
        <>
          <HeroSection />
          <RecommendedDishes />
          <FusionDishes />
          <div className="bg-yellow-50 py-16">
            <div className="max-w-4xl mx-auto text-center px-4">
              <h2 className="text-3xl font-bold text-gray-900 mb-4">Ready to Dine?</h2>
              <p className="text-lg text-gray-600 mb-8">Book your table today and experience the magic of Little Lemon</p>
              <button
                onClick={() => setActiveSection('reservations')}
                className="bg-yellow-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-yellow-700 transition-colors"
              >
                Make a Reservation
              </button>
            </div>
          </div>
        </>
      )}
      
      {activeSection === 'menu' && <MenuSection />}
      {activeSection === 'reservations' && <ReservationSection />}
      {activeSection === 'about' && <AboutSection />}
      {activeSection === 'contact' && <ContactSection />}
      
      <Footer />
    </div>
  );
};

export default LittleLemonRestaurant;
