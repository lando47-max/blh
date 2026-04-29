import React, { useState, useEffect } from 'react';
import { 
  Clock, 
  Sparkles, 
  Heart, 
  MapPin, 
  Phone, 
  ArrowRight, 
  CheckCircle2, 
  Menu, 
  X,
  Droplets,
  Truck,
  Building2,
  Instagram,
  Facebook
} from 'lucide-react';

const App = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => setScrolled(window.scrollY > 50);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const navLinks = [
    { name: 'Services', href: '#services' },
    { name: 'Why Us', href: '#why-us' },
    { name: 'Location', href: '#location' },
    { name: 'Contact', href: '#contact' },
  ];

  return (
    <div className="min-h-screen bg-slate-50 font-sans text-slate-800 selection:bg-purple-100 selection:text-purple-900">
      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${scrolled ? 'bg-white/80 backdrop-blur-md shadow-sm py-3' : 'bg-transparent py-6'}`}>
        <div className="max-w-7xl mx-auto px-6 flex justify-between items-center">
          <div className="flex items-center gap-2 group cursor-pointer">
            <div className="w-10 h-10 bg-gradient-to-br from-cyan-400 to-purple-500 rounded-xl flex items-center justify-center shadow-lg group-hover:rotate-12 transition-transform">
              <Sparkles className="text-white w-6 h-6" />
            </div>
            <span className="text-xl font-bold tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-cyan-600 to-purple-600">
              Lavanderia Express
            </span>
          </div>

          <div className="hidden md:flex items-center gap-8">
            {navLinks.map((link) => (
              <a key={link.name} href={link.href} className="text-sm font-medium hover:text-cyan-600 transition-colors">
                {link.name}
              </a>
            ))}
            <button className="bg-slate-900 text-white px-5 py-2.5 rounded-full text-sm font-semibold hover:bg-slate-800 transition-all hover:shadow-lg active:scale-95">
              Start Your Wash
            </button>
          </div>

          <button className="md:hidden" onClick={() => setIsMenuOpen(!isMenuOpen)}>
            {isMenuOpen ? <X /> : <Menu />}
          </button>
        </div>

        {/* Mobile Menu */}
        {isMenuOpen && (
          <div className="md:hidden absolute top-full left-0 w-full bg-white border-t p-6 flex flex-col gap-4 shadow-xl">
            {navLinks.map((link) => (
              <a key={link.name} href={link.href} className="text-lg font-medium" onClick={() => setIsMenuOpen(false)}>
                {link.name}
              </a>
            ))}
            <button className="bg-cyan-600 text-white p-4 rounded-xl font-bold">Experience Freshness</button>
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <header className="relative pt-32 pb-20 md:pt-48 md:pb-32 overflow-hidden">
        <div className="absolute top-0 left-0 w-full h-full -z-10">
          <div className="absolute top-[-10%] right-[-10%] w-[50%] h-[50%] bg-purple-100 rounded-full blur-[120px] opacity-60"></div>
          <div className="absolute bottom-[-10%] left-[-10%] w-[50%] h-[50%] bg-cyan-100 rounded-full blur-[120px] opacity-60"></div>
        </div>

        <div className="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
          <div className="space-y-8">
            <div className="inline-flex items-center gap-2 px-3 py-1 bg-white border border-slate-200 rounded-full shadow-sm">
              <span className="flex h-2 w-2 rounded-full bg-cyan-500 animate-pulse"></span>
              <span className="text-xs font-bold uppercase tracking-widest text-slate-500">24/7 Premium Service in Brooklyn</span>
            </div>
            <h1 className="text-5xl md:text-7xl font-bold leading-[1.1] text-slate-900">
              Laundry, <br />
              <span className="bg-clip-text text-transparent bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-600">Elevated.</span>
            </h1>
            <p className="text-lg md:text-xl text-slate-600 leading-relaxed max-w-lg">
              Open 24 hours to keep your life flowing clean and easy. Fast service, spotless results, and a friendly neighborhood touch — that’s Lavanderia Express.
            </p>
            <div className="flex flex-col sm:flex-row gap-4 pt-4">
              <button className="bg-slate-900 text-white px-8 py-4 rounded-full font-bold text-lg hover:bg-slate-800 transition-all hover:shadow-xl hover:-translate-y-1 flex items-center justify-center gap-2">
                Experience the Freshness <ArrowRight className="w-5 h-5" />
              </button>
              <a href="#location" className="bg-white text-slate-700 border border-slate-200 px-8 py-4 rounded-full font-bold text-lg hover:bg-slate-50 transition-all flex items-center justify-center gap-2">
                Visit Our Location
              </a>
            </div>
          </div>
          <div className="relative group">
            <div className="absolute inset-0 bg-gradient-to-tr from-cyan-400 to-purple-500 rounded-[2.5rem] rotate-3 opacity-20 blur-2xl group-hover:rotate-6 transition-transform"></div>
            <div className="relative aspect-square md:aspect-[4/5] rounded-[2rem] overflow-hidden shadow-2xl border-8 border-white">
              {/* Primary facility image showing clean modern washers */}
              <img 
                src="https://images.unsplash.com/photo-1517677208171-0bc6725a3e60?auto=format&fit=crop&q=80&w=1200" 
                alt="Modern row of clean stainless steel washers and dryers"
                className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105"
              />
              <div className="absolute bottom-6 left-6 right-6 bg-white/90 backdrop-blur-md p-4 rounded-2xl flex items-center gap-4 border border-white/50">
                <div className="w-12 h-12 bg-cyan-100 rounded-full flex items-center justify-center">
                  <Droplets className="text-cyan-600" />
                </div>
                <div>
                  <p className="text-sm font-bold text-slate-900">Modern Facilities</p>
                  <p className="text-xs text-slate-500">High-efficiency machines for every load</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </header>

      {/* Value Prop Section */}
      <section id="why-us" className="py-24 bg-white">
        <div className="max-w-7xl mx-auto px-6">
          <div className="text-center space-y-4 mb-16">
            <h2 className="text-3xl md:text-5xl font-bold text-slate-900">Why New Yorkers Choose Us</h2>
            <div className="w-20 h-1.5 bg-gradient-to-r from-cyan-400 to-purple-500 mx-auto rounded-full"></div>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            {[
              { icon: <Clock />, title: "24/7 Convenience", desc: "Because clean clothes shouldn’t wait — we’re always open for your schedule." },
              { icon: <Sparkles />, title: "Impeccable Cleanliness", desc: "Every machine, every load, every time — maintained to absolute perfection." },
              { icon: <Heart />, title: "Warm, Local Care", desc: "A friendly face, a helping hand, and service that feels personal to Brooklyn." }
            ].map((item, idx) => (
              <div key={idx} className="p-8 rounded-3xl bg-slate-50 border border-slate-100 hover:border-cyan-200 hover:bg-white hover:shadow-xl transition-all duration-300 group">
                <div className="w-14 h-14 bg-white rounded-2xl shadow-sm flex items-center justify-center text-cyan-600 mb-6 group-hover:scale-110 transition-transform">
                  {item.icon}
                </div>
                <h3 className="text-xl font-bold mb-3 text-slate-900">{item.title}</h3>
                <p className="text-slate-600 leading-relaxed">{item.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Services Section */}
      <section id="services" className="py-24 bg-slate-50">
        <div className="max-w-7xl mx-auto px-6">
          <div className="mb-16">
            <h2 className="text-3xl md:text-5xl font-bold text-slate-900">Services Tailored to Your Schedule</h2>
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
            {[
              { icon: <Sparkles />, title: "Self-Service Laundry", text: "Spacious, spotless, and fully attended — enjoy free Wi-Fi and a stress-free wash." },
              { icon: <CheckCircle2 />, title: "Wash & Fold", text: "Drop it off, breathe easy, and pick up crisp, folded freshness the same day." },
              { icon: <Truck />, title: "Pickup & Delivery", text: "Busy? We’ll come to you and return your laundry cleaner than ever." },
              { icon: <Building2 />, title: "Commercial Laundry", text: "Fast, reliable bulk cleaning for businesses that value consistency and care." }
            ].map((service, i) => (
              <div key={i} className={`p-8 rounded-3xl transition-all duration-300 ${i % 2 === 0 ? 'bg-white shadow-sm' : 'bg-gradient-to-br from-cyan-50 to-blue-50 border border-cyan-100'}`}>
                <div className="text-cyan-600 mb-6">{service.icon}</div>
                <h3 className="text-xl font-bold mb-4">{service.title}</h3>
                <p className="text-slate-600 text-sm leading-relaxed mb-6">{service.text}</p>
                <button className="text-slate-900 font-bold text-sm flex items-center gap-1 group">
                  Learn more <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
                </button>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Testimonial Section */}
      <section className="py-24 bg-slate-900 relative overflow-hidden">
        <div className="absolute top-0 right-0 w-[400px] h-[400px] bg-yellow-500/10 rounded-full blur-[100px]"></div>
        <div className="max-w-7xl mx-auto px-6 relative z-10">
          <div className="grid md:grid-cols-2 gap-16 items-center">
            <div className="grid grid-cols-2 gap-4">
              <img src="https://images.unsplash.com/photo-1545173168-9f18c8fbca82?auto=format&fit=crop&q=80&w=600" className="rounded-2xl h-64 w-full object-cover mt-8 shadow-2xl" alt="Clean washers" />
              <img src="https://images.unsplash.com/photo-1489274495757-95c7c837b101?auto=format&fit=crop&q=80&w=600" className="rounded-2xl h-64 w-full object-cover shadow-2xl" alt="Freshly folded clothes" />
            </div>
            <div className="space-y-8">
              <h2 className="text-3xl md:text-5xl font-bold text-white">Trusted by Brooklyn — <br /><span className="text-cyan-400">Loved by Locals.</span></h2>
              <div className="space-y-6">
                {[
                  { text: "Super clean and friendly! Even late at night, the team made me feel safe and welcome. My clothes have never smelled this fresh.", author: "Sarah J., Bushwick" },
                  { text: "The pickup service is a lifesaver. Reliable, fast, and they actually follow my delicate-wash instructions.", author: "Mike T., East New York" }
                ].map((testimonial, idx) => (
                  <div key={idx} className="bg-white/5 backdrop-blur-sm border border-white/10 p-6 rounded-2xl">
                    <div className="flex gap-1 text-yellow-400 mb-4">
                      {[...Array(5)].map((_, i) => <Sparkles key={i} className="w-4 h-4 fill-current" />)}
                    </div>
                    <p className="text-white/80 italic mb-4 leading-relaxed">"{testimonial.text}"</p>
                    <p className="text-white font-bold">— {testimonial.author}</p>
                  </div>
                ))}
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Location Section */}
      <section id="location" className="py-24 bg-white">
        <div className="max-w-7xl mx-auto px-6">
          <div className="grid md:grid-cols-2 gap-12 items-center bg-slate-50 rounded-[3rem] overflow-hidden p-8 md:p-16 border border-slate-100">
            <div className="space-y-8">
              <h2 className="text-4xl font-bold text-slate-900">Visit Our Brooklyn Flagship</h2>
              <p className="text-slate-600 text-lg leading-relaxed">
                Always open. Always clean. Always here for the heart of Brooklyn. Stop by today or schedule a pickup.
              </p>
              
              <div className="space-y-4">
                <div className="flex items-start gap-4">
                  <div className="w-10 h-10 bg-cyan-100 rounded-full flex items-center justify-center flex-shrink-0">
                    <MapPin className="text-cyan-600" />
                  </div>
                  <div>
                    <h4 className="font-bold">Address</h4>
                    <p className="text-slate-600">2835 Fulton St, Brooklyn, NY 11207</p>
                  </div>
                </div>
                <div className="flex items-start gap-4">
                  <div className="w-10 h-10 bg-purple-100 rounded-full flex items-center justify-center flex-shrink-0">
                    <Phone className="text-purple-600" />
                  </div>
                  <div>
                    <h4 className="font-bold">Phone</h4>
                    <p className="text-slate-600">(718) 827-7169</p>
                  </div>
                </div>
                <div className="flex items-start gap-4">
                  <div className="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center flex-shrink-0">
                    <Clock className="text-green-600" />
                  </div>
                  <div>
                    <h4 className="font-bold">Hours</h4>
                    <p className="text-slate-600">Open 24 hours / 7 days a week</p>
                  </div>
                </div>
              </div>

              <button className="bg-slate-900 text-white px-8 py-4 rounded-full font-bold text-lg hover:bg-slate-800 transition-all flex items-center gap-2">
                Get Directions <MapPin className="w-5 h-5" />
              </button>
            </div>
            
            <div className="h-[400px] bg-slate-200 rounded-3xl overflow-hidden relative grayscale hover:grayscale-0 transition-all duration-700">
              <div className="absolute inset-0 bg-[url('https://api.mapbox.com/styles/v1/mapbox/light-v10/static/-73.89,40.67,13,0/600x400?access_token=pk.eyJ1IjoiZXhhbXBsZSIsImEiOiJjbGV4YW1wbGUifQ')] bg-cover bg-center"></div>
              <div className="absolute inset-0 flex items-center justify-center">
                <div className="w-12 h-12 bg-purple-600 rounded-full flex items-center justify-center text-white animate-bounce shadow-2xl border-4 border-white">
                  <MapPin className="w-6 h-6" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Final CTA */}
      <section className="py-20 px-6">
        <div className="max-w-5xl mx-auto bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 rounded-[3rem] p-12 md:p-20 text-center text-white relative overflow-hidden shadow-2xl">
          <div className="absolute top-0 left-0 w-full h-full opacity-10 pointer-events-none">
            <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" className="w-full h-full">
              <path fill="#FFFFFF" d="M45.2,-77.2C58.4,-70.7,69.1,-58.5,76.5,-44.7C83.9,-30.9,88.1,-15.5,88.2,0.1C88.4,15.6,84.4,31.2,76.5,45.2C68.6,59.3,56.8,71.8,42.8,78.5C28.8,85.2,14.4,86,0.3,85.5C-13.8,85,-27.6,83.1,-41.4,77.3C-55.2,71.5,-69,61.8,-77.8,48.8C-86.7,35.8,-90.6,19.4,-90.2,3.3C-89.9,-12.8,-85.2,-28.6,-77.1,-43.1C-69,-57.6,-57.5,-70.8,-43.8,-76.8C-30,-82.8,-15,-81.7,0.1,-81.9C15.2,-82.1,32,-83.7,45.2,-77.2Z" transform="translate(100 100)" />
            </svg>
          </div>
          <h2 className="text-4xl md:text-6xl font-bold mb-6">Laundry, Simplified.</h2>
          <p className="text-xl md:text-2xl text-white/90 mb-10 max-w-2xl mx-auto">
            Drop it off, or let us pick it up — your cleanest clothes await. Experience the Brooklyn standard.
          </p>
          <button className="bg-white text-blue-600 px-10 py-5 rounded-full font-black text-xl hover:shadow-2xl hover:scale-105 active:scale-95 transition-all">
            Start Your Wash →
          </button>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-white pt-20 pb-10 border-t border-slate-100">
        <div className="max-w-7xl mx-auto px-6">
          <div className="grid md:grid-cols-4 gap-12 mb-16">
            <div className="col-span-1 md:col-span-1 space-y-6">
              <div className="flex items-center gap-2">
                <div className="w-8 h-8 bg-gradient-to-br from-cyan-400 to-purple-500 rounded-lg flex items-center justify-center">
                  <Sparkles className="text-white w-4 h-4" />
                </div>
                <span className="font-bold text-xl text-slate-900">Lavanderia Express</span>
              </div>
              <p className="text-slate-500 text-sm leading-relaxed">
                Clean clothes, made easy. 24/7 service in Brooklyn for over 10 years.
              </p>
              <div className="flex gap-4">
                <a href="#" className="w-10 h-10 bg-slate-50 rounded-full flex items-center justify-center text-slate-400 hover:text-cyan-600 transition-colors">
                  <Instagram className="w-5 h-5" />
                </a>
                <a href="#" className="w-10 h-10 bg-slate-50 rounded-full flex items-center justify-center text-slate-400 hover:text-cyan-600 transition-colors">
                  <Facebook className="w-5 h-5" />
                </a>
              </div>
            </div>
            
            <div>
              <h4 className="font-bold mb-6">Quick Links</h4>
              <ul className="space-y-4 text-sm text-slate-500">
                <li><a href="#services" className="hover:text-cyan-600 transition-colors">Services</a></li>
                <li><a href="#location" className="hover:text-cyan-600 transition-colors">Location</a></li>
                <li><a href="#" className="hover:text-cyan-600 transition-colors">Wash & Fold</a></li>
                <li><a href="#" className="hover:text-cyan-600 transition-colors">Delivery Area</a></li>
              </ul>
            </div>

            <div>
              <h4 className="font-bold mb-6">Company</h4>
              <ul className="space-y-4 text-sm text-slate-500">
                <li><a href="#" className="hover:text-cyan-600 transition-colors">About Us</a></li>
                <li><a href="#" className="hover:text-cyan-600 transition-colors">Careers</a></li>
                <li><a href="#" className="hover:text-cyan-600 transition-colors">Contact</a></li>
                <li><a href="#" className="hover:text-cyan-600 transition-colors">Reviews</a></li>
              </ul>
            </div>

            <div>
              <h4 className="font-bold mb-6">Contact</h4>
              <ul className="space-y-4 text-sm text-slate-500">
                <li className="flex items-center gap-3"><Phone className="w-4 h-4" /> (718) 827‑7169</li>
                <li className="flex items-center gap-3"><MapPin className="w-4 h-4" /> 2835 Fulton St, Brooklyn</li>
                <li className="flex items-center gap-3"><Clock className="w-4 h-4" /> Open 24 Hours</li>
              </ul>
            </div>
          </div>
          
          <div className="pt-8 border-t border-slate-100 flex flex-col md:flex-row justify-between items-center gap-4 text-xs text-slate-400">
            <p>© 2026 Lavanderia Express Corp | All rights reserved.</p>
            <div className="flex gap-6">
              <a href="#" className="hover:text-slate-600">Privacy Policy</a>
              <a href="#" className="hover:text-slate-600">Terms & Conditions</a>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default App;
