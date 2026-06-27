# 🚀 Super Prompt para OpenCode - Mejora Completa de Identidad_AHA

```markdown
# CONTEXTO DEL PROYECTO

Eres un desarrollador frontend experto trabajando en la landing page "Identidad_AHA" (https://angelhdz84.github.io/Identidad_AHA/), una página que presenta apps offline-first para negocios.

**Stack Tecnológico (OBLIGATORIO):**
- HTML5 semántico
- CSS3 + Tailwind CSS (CDN)
- JavaScript ES6+ (vanilla)
- Alpine.js (reactividad)
- Dexie.js (IndexedDB wrapper)
- Bootstrap Icons
- Animate.css
- ApexCharts (si se necesitan gráficos)
- jsPDF + SheetJS (funcionalidades de exportación)
- CryptoJS (cifrado)
- LocalStorage (persistencia)

**Principios de Diseño:**
- Mobile-first responsive
- Offline-first (todo debe funcionar sin internet)
- Performance-first (sin dependencias pesadas)
- Accesibilidad WCAG 2.1 AA
- UX simple e intuitiva

---

# PROBLEMAS IDENTIFICADOS A RESOLVER

1. **Confusión bilingüe**: Texto en ES/EN simultáneo sin selector
2. **Sobrecarga técnica**: Snippets de código visibles que intimidan usuarios no técnicos
3. **Falta de social proof**: Sin testimonios reales ni casos de estudio
4. **Sin demos interactivas**: Usuario no puede probar antes de comprar
5. **Proceso de compra poco claro**: Botones sin funcionalidad
6. **Navegación limitada**: Sin menú fijo ni smooth scroll
7. **CTAs débiles**: Sin urgencia ni incentivos claros

---

# PLAN DE IMPLEMENTACIÓN POR FASES

## FASE 1: FUNDAMENTOS UX (PRIORIDAD ALTA)

### 1.1 Sistema de Traducción ES/EN
**Objetivo:** Toggle de idioma en header que guarde preferencia en localStorage

**Requisitos técnicos:**
```javascript
// Estructura de traducciones
const translations = {
  es: {
    hero_title: "Apps Offline-First para tu Negocio",
    hero_subtitle: "Sin internet, sin mensualidades, sin complicaciones",
    // ... más traducciones
  },
  en: {
    hero_title: "Offline-First Apps for Your Business",
    hero_subtitle: "No internet, no monthly fees, no complications",
    // ... más traducciones
  }
};

// Alpine.js store para manejar idioma
Alpine.store('lang', {
  current: localStorage.getItem('lang') || 'es',
  toggle() {
    this.current = this.current === 'es' ? 'en' : 'es';
    localStorage.setItem('lang', this.current);
  },
  t(key) {
    return translations[this.current][key] || key;
  }
});
```

**HTML del toggle:**
```html
<button 
  x-data 
  @click="$store.lang.toggle()"
  class="flex items-center gap-2 px-4 py-2 bg-gray-100 rounded-lg hover:bg-gray-200 transition"
  aria-label="Cambiar idioma"
>
  <span x-show="$store.lang.current === 'es'" class="text-2xl">🇪🇸</span>
  <span x-show="$store.lang.current === 'en'" class="text-2xl">🇬🇧</span>
  <span class="font-medium" x-text="$store.lang.current === 'es' ? 'English' : 'Español'"></span>
</button>
```

**Uso en elementos:**
```html
<h1 x-text="$store.lang.t('hero_title')"></h1>
<p x-text="$store.lang.t('hero_subtitle')"></p>
```

**Criterios de aceptación:**
- ✅ Toggle visible en header (esquina superior derecha)
- ✅ Cambio instantáneo sin recarga
- ✅ Preferencia persiste al recargar
- ✅ Todo el contenido traducido
- ✅ Accesible con teclado

---

### 1.2 Navegación Fija con Smooth Scroll
**Objetivo:** Navbar sticky que se mantenga visible al hacer scroll

**Requisitos:**
```html
<nav 
  x-data="{ scrolled: false, mobileOpen: false }"
  @scroll.window="scrolled = window.scrollY > 50"
  :class="scrolled ? 'bg-white shadow-lg' : 'bg-transparent'"
  class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
>
  <div class="container mx-auto px-4">
    <div class="flex items-center justify-between h-16">
      <!-- Logo -->
      <a href="#inicio" class="font-bold text-xl">AHA Apps</a>
      
      <!-- Desktop Menu -->
      <div class="hidden md:flex items-center gap-6">
        <a href="#apps" class="hover:text-blue-600 transition" x-text="$store.lang.t('nav_apps')">Apps</a>
        <a href="#pricing" class="hover:text-blue-600 transition" x-text="$store.lang.t('nav_pricing')">Precios</a>
        <a href="#process" class="hover:text-blue-600 transition" x-text="$store.lang.t('nav_process')">Proceso</a>
        <a href="#faq" class="hover:text-blue-600 transition" x-text="$store.lang.t('nav_faq')">FAQ</a>
        <a href="#contact" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition" x-text="$store.lang.t('nav_contact')">Contacto</a>
      </div>
      
      <!-- Mobile Menu Button -->
      <button 
        @click="mobileOpen = !mobileOpen"
        class="md:hidden p-2"
        aria-label="Menú"
      >
        <i class="bi bi-list text-2xl"></i>
      </button>
    </div>
    
    <!-- Mobile Menu -->
    <div x-show="mobileOpen" x-transition class="md:hidden py-4">
      <a href="#apps" @click="mobileOpen = false" class="block py-2" x-text="$store.lang.t('nav_apps')">Apps</a>
      <a href="#pricing" @click="mobileOpen = false" class="block py-2" x-text="$store.lang.t('nav_pricing')">Precios</a>
      <a href="#process" @click="mobileOpen = false" class="block py-2" x-text="$store.lang.t('nav_process')">Proceso</a>
      <a href="#faq" @click="mobileOpen = false" class="block py-2" x-text="$store.lang.t('nav_faq')">FAQ</a>
      <a href="#contact" @click="mobileOpen = false" class="block py-2 text-blue-600 font-semibold" x-text="$store.lang.t('nav_contact')">Contacto</a>
    </div>
  </div>
</nav>
```

**CSS adicional:**
```css
html {
  scroll-behavior: smooth;
  scroll-padding-top: 80px; /* Compensar navbar fija */
}
```

**Criterios de aceptación:**
- ✅ Navbar fija en top
- ✅ Cambio de estilo al hacer scroll
- ✅ Smooth scroll a secciones
- ✅ Menú hamburguesa en móvil
- ✅ Se cierra al hacer click en enlace

---

### 1.3 Optimización Mobile-First
**Objetivo:** Asegurar que todo funcione perfectamente en móvil

**Requisitos de responsive:**
```css
/* Grid de apps */
.apps-grid {
  display: grid;
  grid-template-columns: 1fr; /* Mobile */
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .apps-grid {
    grid-template-columns: repeat(2, 1fr); /* Tablet */
  }
}

@media (min-width: 1024px) {
  .apps-grid {
    grid-template-columns: repeat(3, 1fr); /* Desktop */
  }
}

/* Tabla comparativa → Cards en móvil */
@media (max-width: 767px) {
  .comparison-table {
    display: none;
  }
  .comparison-cards {
    display: block;
  }
}

@media (min-width: 768px) {
  .comparison-table {
    display: table;
  }
  .comparison-cards {
    display: none;
  }
}

/* Botones touch-friendly */
button, a.btn {
  min-height: 44px;
  min-width: 44px;
}

/* FAQ acordeón */
.faq-item {
  border-bottom: 1px solid #e5e7eb;
}

.faq-question {
  padding: 1rem;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.faq-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
}

.faq-item.active .faq-answer {
  max-height: 500px;
}
```

**Criterios de aceptación:**
- ✅ Todo legible en pantallas 320px+
- ✅ Botones fácilmente clickeables (44px mínimo)
- ✅ Sin scroll horizontal
- ✅ Imágenes optimizadas
- ✅ Textos no se cortan

---

## FASE 2: MEJORAS DE CONVERSIÓN (PRIORIDAD ALTA)

### 2.1 Demo Interactiva de FacturaExpress
**Objetivo:** Permitir probar la app directamente en la landing

**Requisitos:**
```html
<section id="demo" class="py-20 bg-gray-50">
  <div class="container mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-12" x-text="$store.lang.t('demo_title')">Prueba FacturaExpress Ahora</h2>
    
    <div 
      x-data="invoiceDemo()"
      class="max-w-4xl mx-auto bg-white rounded-xl shadow-lg p-8"
    >
      <!-- Formulario de demo -->
      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label class="block mb-2 font-semibold" x-text="$store.lang.t('demo_product')">Producto</label>
          <input 
            x-model="product"
            type="text" 
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500"
            placeholder="Ej: Consultoría"
          >
        </div>
        
        <div>
          <label class="block mb-2 font-semibold" x-text="$store.lang.t('demo_quantity')">Cantidad</label>
          <input 
            x-model.number="quantity"
            type="number" 
            min="1"
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500"
          >
        </div>
        
        <div>
          <label class="block mb-2 font-semibold" x-text="$store.lang.t('demo_price')">Precio Unitario (€)</label>
          <input 
            x-model.number="price"
            type="number" 
            min="0"
            step="0.01"
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500"
          >
        </div>
        
        <div>
          <label class="block mb-2 font-semibold" x-text="$store.lang.t('demo_tax')">IVA (%)</label>
          <input 
            x-model.number="tax"
            type="number" 
            min="0"
            class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-blue-500"
          >
        </div>
      </div>
      
      <!-- Resultado en tiempo real -->
      <div class="mt-8 p-6 bg-blue-50 rounded-lg">
        <div class="flex justify-between mb-2">
          <span>Subtotal:</span>
          <span class="font-semibold" x-text="`€${subtotal.toFixed(2)}`"></span>
        </div>
        <div class="flex justify-between mb-2">
          <span>IVA:</span>
          <span class="font-semibold" x-text="`€${taxAmount.toFixed(2)}`"></span>
        </div>
        <div class="flex justify-between text-xl font-bold pt-4 border-t">
          <span>Total:</span>
          <span class="text-blue-600" x-text="`€${total.toFixed(2)}`"></span>
        </div>
      </div>
      
      <!-- Botones de acción -->
      <div class="mt-6 flex gap-4">
        <button 
          @click="generatePDF()"
          class="flex-1 bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition font-semibold"
        >
          <i class="bi bi-file-earmark-pdf mr-2"></i>
          <span x-text="$store.lang.t('demo_generate_pdf')">Generar PDF</span>
        </button>
        
        <button 
          @click="resetDemo()"
          class="px-6 py-3 border-2 border-gray-300 rounded-lg hover:bg-gray-50 transition"
        >
          <i class="bi bi-arrow-counterclockwise mr-2"></i>
          <span x-text="$store.lang.t('demo_reset')">Reiniciar</span>
        </button>
      </div>
    </div>
  </div>
</section>
```

**JavaScript de la demo:**
```javascript
function invoiceDemo() {
  return {
    product: 'Consultoría',
    quantity: 1,
    price: 100,
    tax: 21,
    
    get subtotal() {
      return this.quantity * this.price;
    },
    
    get taxAmount() {
      return this.subtotal * (this.tax / 100);
    },
    
    get total() {
      return this.subtotal + this.taxAmount;
    },
    
    generatePDF() {
      // Usar jsPDF para generar PDF
      const { jsPDF } = window.jspdf;
      const doc = new jsPDF();
      
      doc.setFontSize(20);
      doc.text('Factura', 20, 20);
      
      doc.setFontSize(12);
      doc.text(`Producto: ${this.product}`, 20, 40);
      doc.text(`Cantidad: ${this.quantity}`, 20, 50);
      doc.text(`Precio: €${this.price.toFixed(2)}`, 20, 60);
      doc.text(`Subtotal: €${this.subtotal.toFixed(2)}`, 20, 70);
      doc.text(`IVA (${this.tax}%): €${this.taxAmount.toFixed(2)}`, 20, 80);
      doc.text(`Total: €${this.total.toFixed(2)}`, 20, 90);
      
      doc.save(`factura-${Date.now()}.pdf`);
      
      // Mostrar notificación
      alert('¡PDF generado exitosamente! Esta es una demo de FacturaExpress.');
    },
    
    resetDemo() {
      this.product = 'Consultoría';
      this.quantity = 1;
      this.price = 100;
      this.tax = 21;
    }
  };
}
```

**Criterios de aceptación:**
- ✅ Cálculo en tiempo real
- ✅ Generación de PDF funcional
- ✅ Sin requerir backend
- ✅ Responsive
- ✅ Feedback visual al generar PDF

---

### 2.2 Sistema de Testimonios
**Objetivo:** Carrusel de testimonios reales con fotos y calificaciones

**Requisitos:**
```html
<section id="testimonials" class="py-20">
  <div class="container mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-12" x-text="$store.lang.t('testimonials_title')">Lo que Dicen Nuestros Clientes</h2>
    
    <div 
      x-data="testimonialCarousel()"
      class="max-w-4xl mx-auto"
    >
      <!-- Testimonios -->
      <div class="relative overflow-hidden">
        <template x-for="(testimonial, index) in testimonials" :key="index">
          <div 
            x-show="current === index"
            x-transition:enter="transition ease-out duration-500"
            x-transition:enter-start="opacity-0 transform translate-x-full"
            x-transition:enter-end="opacity-100 transform translate-x-0"
            x-transition:leave="transition ease-in duration-500"
            x-transition:leave-start="opacity-100 transform translate-x-0"
            x-transition:leave-end="opacity-0 transform -translate-x-full"
            class="bg-white rounded-xl shadow-lg p-8"
          >
            <div class="flex items-center mb-4">
              <img 
                :src="testimonial.avatar" 
                :alt="testimonial.name"
                class="w-16 h-16 rounded-full mr-4"
              >
              <div>
                <h3 class="font-bold text-lg" x-text="testimonial.name"></h3>
                <p class="text-gray-600" x-text="testimonial.company"></p>
                <div class="flex text-yellow-400 mt-1">
                  <template x-for="star in 5">
                    <i :class="star <= testimonial.rating ? 'bi bi-star-fill' : 'bi bi-star'"></i>
                  </template>
                </div>
              </div>
            </div>
            
            <p class="text-gray-700 italic" x-text="testimonial.text"></p>
            
            <div class="mt-4 text-sm text-gray-500">
              <i class="bi bi-geo-alt"></i>
              <span x-text="testimonial.country"></span>
            </div>
          </div>
        </template>
      </div>
      
      <!-- Controles -->
      <div class="flex justify-center items-center mt-6 gap-4">
        <button 
          @click="prev()"
          class="p-2 rounded-full bg-gray-200 hover:bg-gray-300 transition"
          :disabled="current === 0"
        >
          <i class="bi bi-chevron-left"></i>
        </button>
        
        <div class="flex gap-2">
          <template x-for="(testimonial, index) in testimonials" :key="index">
            <button 
              @click="current = index"
              :class="current === index ? 'bg-blue-600' : 'bg-gray-300'"
              class="w-3 h-3 rounded-full transition"
            ></button>
          </template>
        </div>
        
        <button 
          @click="next()"
          class="p-2 rounded-full bg-gray-200 hover:bg-gray-300 transition"
          :disabled="current === testimonials.length - 1"
        >
          <i class="bi bi-chevron-right"></i>
        </button>
      </div>
    </div>
  </div>
</section>
```

**JavaScript del carrusel:**
```javascript
function testimonialCarousel() {
  return {
    current: 0,
    testimonials: [
      {
        name: 'María González',
        company: 'Clínica Dental Sonríe',
        country: 'España',
        avatar: 'https://i.pravatar.cc/150?img=1',
        rating: 5,
        text: 'FacturaExpress me ahorró horas de trabajo cada semana. Lo mejor es que funciona sin internet, perfecto para mi clínica.'
      },
      {
        name: 'Carlos Rodríguez',
        company: 'Taller Mecánico AutoFix',
        country: 'México',
        avatar: 'https://i.pravatar.cc/150?img=3',
        rating: 5,
        text: 'La inversión se pagó sola en el primer mes. Ahora tengo todo organizado y mis clientes están más satisfechos.'
      },
      {
        name: 'Ana Martínez',
        company: 'Consultoría Financiera',
        country: 'Colombia',
        avatar: 'https://i.pravatar.cc/150?img=5',
        rating: 5,
        text: 'Excelente soporte y la app funciona perfectamente. La capacidad de cifrar datos me da total tranquilidad.'
      }
    ],
    
    next() {
      if (this.current < this.testimonials.length - 1) {
        this.current++;
      }
    },
    
    prev() {
      if (this.current > 0) {
        this.current--;
      }
    }
  };
}
```

**Criterios de aceptación:**
- ✅ Animaciones suaves
- ✅ Responsive
- ✅ Controles de navegación
- ✅ Indicadores de posición
- ✅ Accesible con teclado

---

### 2.3 Botón Flotante de WhatsApp
**Objetivo:** Botón siempre visible que abra WhatsApp con mensaje contextual

**Requisitos:**
```html
<div 
  x-data="{ open: false, context: '' }"
  class="fixed bottom-6 right-6 z-50"
>
  <!-- Chat widget -->
  <div 
    x-show="open"
    x-transition:enter="transition ease-out duration-300"
    x-transition:enter-start="opacity-0 transform scale-90"
    x-transition:enter-end="opacity-100 transform scale-100"
    x-transition:leave="transition ease-in duration-200"
    x-transition:leave-start="opacity-100 transform scale-100"
    x-transition:leave-end="opacity-0 transform scale-90"
    class="mb-4 bg-white rounded-xl shadow-2xl p-6 w-80"
  >
    <div class="flex items-center mb-4">
      <img src="https://i.pravatar.cc/150?img=10" alt="Soporte" class="w-12 h-12 rounded-full mr-3">
      <div>
        <h3 class="font-bold">¿Necesitas ayuda?</h3>
        <p class="text-sm text-gray-600">Respondemos en minutos</p>
      </div>
    </div>
    
    <div class="space-y-2">
      <button 
        @click="openWhatsApp('pricing')"
        class="w-full text-left p-3 bg-gray-50 rounded-lg hover:bg-gray-100 transition"
      >
        <i class="bi bi-cash-coin text-green-600 mr-2"></i>
        <span x-text="$store.lang.t('whatsapp_pricing')">Consultar precios</span>
      </button>
      
      <button 
        @click="openWhatsApp('demo')"
        class="w-full text-left p-3 bg-gray-50 rounded-lg hover:bg-gray-100 transition"
      >
        <i class="bi bi-play-circle text-blue-600 mr-2"></i>
        <span x-text="$store.lang.t('whatsapp_demo')">Solicitar demo</span>
      </button>
      
      <button 
        @click="openWhatsApp('support')"
        class="w-full text-left p-3 bg-gray-50 rounded-lg hover:bg-gray-100 transition"
      >
        <i class="bi bi-question-circle text-purple-600 mr-2"></i>
        <span x-text="$store.lang.t('whatsapp_support')">Soporte técnico</span>
      </button>
    </div>
  </div>
  
  <!-- Botón principal -->
  <button 
    @click="open = !open"
    class="w-16 h-16 bg-green-500 text-white rounded-full shadow-lg hover:bg-green-600 transition transform hover:scale-110"
    aria-label="Contactar por WhatsApp"
  >
    <i class="bi bi-whatsapp text-3xl"></i>
  </button>
</div>
```

**JavaScript:**
```javascript
function whatsappWidget() {
  return {
    phoneNumber: '34XXXXXXXXX', // Reemplazar con número real
    
    openWhatsApp(context) {
      const messages = {
        pricing: 'Hola! Me interesa conocer los precios de las apps offline.',
        demo: 'Hola! Me gustaría solicitar una demo de las apps.',
        support: 'Hola! Necesito soporte técnico.'
      };
      
      const message = encodeURIComponent(messages[context] || 'Hola! Necesito información.');
      const url = `https://wa.me/${this.phoneNumber}?text=${message}`;
      
      window.open(url, '_blank');
      
      // Trackear conversión
      this.trackConversion(context);
    },
    
    trackConversion(context) {
      const conversions = JSON.parse(localStorage.getItem('conversions') || '[]');
      conversions.push({
        type: 'whatsapp',
        context: context,
        timestamp: new Date().toISOString()
      });
      localStorage.setItem('conversions', JSON.stringify(conversions));
    }
  };
}
```

**Criterios de aceptación:**
- ✅ Siempre visible
- ✅ No bloquea contenido
- ✅ Mensajes contextuales
- ✅ Tracking de conversiones
- ✅ Responsive

---

### 2.4 Calculadora de Precios Interactiva
**Objetivo:** Permitir al usuario calcular precio según sus necesidades

**Requisitos:**
```html
<section id="calculator" class="py-20 bg-gradient-to-br from-blue-50 to-purple-50">
  <div class="container mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-4" x-text="$store.lang.t('calculator_title')">Calcula tu Inversión</h2>
    <p class="text-center text-gray-600 mb-12" x-text="$store.lang.t('calculator_subtitle')">Personaliza según tus necesidades</p>
    
    <div 
      x-data="priceCalculator()"
      class="max-w-4xl mx-auto bg-white rounded-xl shadow-lg p-8"
    >
      <div class="grid md:grid-cols-2 gap-8">
        <!-- Opciones -->
        <div>
          <h3 class="font-bold text-xl mb-4" x-text="$store.lang.t('calculator_modules')">Módulos Requeridos</h3>
          
          <div class="space-y-3">
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="modules.facturacion" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('module_billing')">Facturación</div>
                <div class="text-sm text-gray-600">€197</div>
              </div>
            </label>
            
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="modules.citas" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('module_appointments')">Citas</div>
                <div class="text-sm text-gray-600">€147</div>
              </div>
            </label>
            
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="modules.inventario" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('module_inventory')">Inventario</div>
                <div class="text-sm text-gray-600">€167</div>
              </div>
            </label>
            
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="modules.clientes" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('module_crm')">CRM Clientes</div>
                <div class="text-sm text-gray-600">€127</div>
              </div>
            </label>
          </div>
          
          <h3 class="font-bold text-xl mt-6 mb-4" x-text="$store.lang.t('calculator_extras')">Extras</h3>
          
          <div class="space-y-3">
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="extras.cifrado" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('extra_encryption')">Cifrado AES-256</div>
                <div class="text-sm text-gray-600">+€97</div>
              </div>
            </label>
            
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="extras.ia" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('extra_ai')">IA Jutia Full</div>
                <div class="text-sm text-gray-600">+€197</div>
              </div>
            </label>
            
            <label class="flex items-center p-3 border rounded-lg hover:bg-gray-50 cursor-pointer">
              <input type="checkbox" x-model="extras.formatos" class="mr-3 w-5 h-5">
              <div>
                <div class="font-semibold" x-text="$store.lang.t('extra_formats')">Formatos .exe + .apk</div>
                <div class="text-sm text-gray-600">+€147</div>
              </div>
            </label>
          </div>
        </div>
        
        <!-- Resultado -->
        <div class="bg-gradient-to-br from-blue-600 to-purple-600 text-white rounded-xl p-8">
          <h3 class="text-2xl font-bold mb-6" x-text="$store.lang.t('calculator_summary')">Resumen</h3>
          
          <div class="space-y-3 mb-6">
            <template x-for="(price, module) in selectedModules" :key="module">
              <div class="flex justify-between">
                <span x-text="module"></span>
                <span x-text="`€${price}`"></span>
              </div>
            </template>
            
            <template x-for="(price, extra) in selectedExtras" :key="extra">
              <div class="flex justify-between">
                <span x-text="extra"></span>
                <span x-text="`€${price}`"></span>
              </div>
            </template>
          </div>
          
          <div class="border-t border-white/30 pt-6">
            <div class="flex justify-between text-lg mb-2">
              <span x-text="$store.lang.t('calculator_subtotal')">Subtotal:</span>
              <span x-text="`€${subtotal}`"></span>
            </div>
            
            <div class="flex justify-between text-3xl font-bold">
              <span>Total:</span>
              <span x-text="`€${total}`"></span>
            </div>
            
            <div class="mt-2 text-sm opacity-80">
              <span x-text="$store.lang.t('calculator_savings')">Ahorras vs SaaS:</span>
              <span class="font-bold" x-text="`€${savings}/año`"></span>
            </div>
          </div>
          
          <button 
            @click="requestQuote()"
            class="w-full mt-6 bg-white text-blue-600 px-6 py-3 rounded-lg font-bold hover:bg-gray-100 transition"
          >
            <i class="bi bi-send mr-2"></i>
            <span x-text="$store.lang.t('calculator_cta')">Solicitar Cotización Exacta</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</section>
```

**JavaScript:**
```javascript
function priceCalculator() {
  return {
    modules: {
      facturacion: false,
      citas: false,
      inventario: false,
      clientes: false
    },
    extras: {
      cifrado: false,
      ia: false,
      formatos: false
    },
    
    prices: {
      modules: {
        facturacion: 197,
        citas: 147,
        inventario: 167,
        clientes: 127
      },
      extras: {
        cifrado: 97,
        ia: 197,
        formatos: 147
      }
    },
    
    get selectedModules() {
      const selected = {};
      for (const [key, value] of Object.entries(this.modules)) {
        if (value) {
          selected[this.getModuleName(key)] = this.prices.modules[key];
        }
      }
      return selected;
    },
    
    get selectedExtras() {
      const selected = {};
      for (const [key, value] of Object.entries(this.extras)) {
        if (value) {
          selected[this.getExtraName(key)] = this.prices.extras[key];
        }
      }
      return selected;
    },
    
    get subtotal() {
      let total = 0;
      for (const [key, value] of Object.entries(this.modules)) {
        if (value) total += this.prices.modules[key];
      }
      for (const [key, value] of Object.entries(this.extras)) {
        if (value) total += this.prices.extras[key];
      }
      return total;
    },
    
    get total() {
      return this.subtotal;
    },
    
    get savings() {
      // Calcular ahorro vs SaaS (asumiendo €50/mes por módulo)
      const monthlySaaS = Object.values(this.modules).filter(v => v).length * 50;
      const annualSaaS = monthlySaaS * 12;
      return Math.max(0, annualSaaS - this.total);
    },
    
    getModuleName(key) {
      const names = {
        facturacion: 'Facturación',
        citas: 'Citas',
        inventario: 'Inventario',
        clientes: 'CRM Clientes'
      };
      return names[key] || key;
    },
    
    getExtraName(key) {
      const names = {
        cifrado: 'Cifrado AES-256',
        ia: 'IA Jutia Full',
        formatos: 'Formatos .exe + .apk'
      };
      return names[key] || key;
    },
    
    requestQuote() {
      const details = {
        modules: this.selectedModules,
        extras: this.selectedExtras,
        total: this.total
      };
      
      localStorage.setItem('quote_request', JSON.stringify(details));
      
      // Abrir WhatsApp con detalles
      const message = encodeURIComponent(`Hola! Me interesa una cotización para:\n\nMódulos: ${Object.keys(this.selectedModules).join(', ')}\nExtras: ${Object.keys(this.selectedExtras).join(', ')}\nTotal estimado: €${this.total}`);
      
      window.open(`https://wa.me/34XXXXXXXXX?text=${message}`, '_blank');
    }
  };
}
```

**Criterios de aceptación:**
- ✅ Cálculo en tiempo real
- ✅ Muestra ahorro vs SaaS
- ✅ Botón de cotización funcional
- ✅ Responsive
- ✅ Persiste selección

---

## FASE 3: REDUCCIÓN DE FRICCIÓN TÉCNICA (PRIORIDAD MEDIA)

### 3.1 Simplificación de Código Visible
**Objetivo:** Reemplazar snippets complejos con diagramas visuales

**Requisitos:**
```html
<!-- ANTES (código complejo) -->
<div class="code-snippet">
  <pre><code>await db.facturas.orderBy('fecha').reverse().toArray()</code></pre>
</div>

<!-- DESPUÉS (diagrama visual) -->
<div class="visual-diagram">
  <div class="flex items-center justify-center gap-4 p-8 bg-gray-50 rounded-xl">
    <div class="text-center">
      <i class="bi bi-window text-4xl text-blue-600"></i>
      <p class="mt-2 font-semibold">Interfaz</p>
    </div>
    
    <i class="bi bi-arrow-right text-2xl text-gray-400"></i>
    
    <div class="text-center">
      <i class="bi bi-database text-4xl text-green-600"></i>
      <p class="mt-2 font-semibold">IndexedDB</p>
    </div>
    
    <i class="bi bi-arrow-right text-2xl text-gray-400"></i>
    
    <div class="text-center">
      <i class="bi bi-shield-lock text-4xl text-purple-600"></i>
      <p class="mt-2 font-semibold">Cifrado</p>
    </div>
  </div>
  
  <p class="text-center text-gray-600 mt-4">
    Tus datos fluyen de forma segura desde la interfaz hasta el almacenamiento local cifrado
  </p>
  
  <!-- Opción para usuarios técnicos -->
  <details class="mt-4">
    <summary class="cursor-pointer text-blue-600 hover:text-blue-700">
      <i class="bi bi-code-slash mr-2"></i>
      Ver código de ejemplo
    </summary>
    <pre class="mt-2 p-4 bg-gray-900 text-gray-100 rounded-lg overflow-x-auto"><code>await db.facturas.orderBy('fecha').reverse().toArray()</code></pre>
  </details>
</div>
```

**Criterios de aceptación:**
- ✅ Diagrama visual claro
- ✅ Código oculto por defecto
- ✅ Explicación en lenguaje natural
- ✅ Accesible para no técnicos

---

## FASE 4: ANALYTICS Y TRACKING (PRIORIDAD MEDIA)

### 4.1 Sistema de Analytics Local
**Objetivo:** Trackear comportamiento sin servidor

**Requisitos:**
```javascript
// analytics.js
const Analytics = {
  init() {
    this.trackPageView();
    this.setupScrollTracking();
    this.setupClickTracking();
  },
  
  trackPageView() {
    this.log({
      type: 'pageview',
      url: window.location.href,
      timestamp: new Date().toISOString()
    });
  },
  
  setupScrollTracking() {
    let maxScroll = 0;
    
    window.addEventListener('scroll', () => {
      const scrollPercent = Math.round(
        (window.scrollY / (document.documentElement.scrollHeight - window.innerHeight)) * 100
      );
      
      if (scrollPercent > maxScroll) {
        maxScroll = scrollPercent;
        
        // Trackear hitos
        if (scrollPercent >= 25 && !this.tracked['25%']) {
          this.trackEvent('scroll', '25%');
          this.tracked['25%'] = true;
        }
        if (scrollPercent >= 50 && !this.tracked['50%']) {
          this.trackEvent('scroll', '50%');
          this.tracked['50%'] = true;
        }
        if (scrollPercent >= 75 && !this.tracked['75%']) {
          this.trackEvent('scroll', '75%');
          this.tracked['75%'] = true;
        }
        if (scrollPercent >= 100 && !this.tracked['100%']) {
          this.trackEvent('scroll', '100%');
          this.tracked['100%'] = true;
        }
      }
    });
  },
  
  setupClickTracking() {
    document.addEventListener('click', (e) => {
      const target = e.target.closest('button, a');
      if (target) {
        this.trackEvent('click', {
          text: target.textContent.trim(),
          href: target.href || '',
          id: target.id || ''
        });
      }
    });
  },
  
  trackEvent(action, data) {
    this.log({
      type: 'event',
      action,
      data,
      timestamp: new Date().toISOString()
    });
  },
  
  log(event) {
    const events = JSON.parse(localStorage.getItem('analytics') || '[]');
    events.push(event);
    
    // Mantener solo últimos 1000 eventos
    if (events.length > 1000) {
      events.splice(0, events.length - 1000);
    }
    
    localStorage.setItem('analytics', JSON.stringify(events));
  },
  
  tracked: {},
  
  exportData() {
    const events = JSON.parse(localStorage.getItem('analytics') || '[]');
    const blob = new Blob([JSON.stringify(events, null, 2)], { type: 'application/json' });
    const url = URL.createObjectURL(blob);
    
    const a = document.createElement('a');
    a.href = url;
    a.download = `analytics-${Date.now()}.json`;
    a.click();
    
    URL.revokeObjectURL(url);
  }
};

// Inicializar
Analytics.init();
```

**Criterios de aceptación:**
- ✅ Sin dependencias externas
- ✅ No envía datos a servidores
- ✅ Exportable a JSON
- ✅ Respeta privacidad
- ✅ Performance óptimo

---

# INSTRUCCIONES FINALES PARA OPENCODE

## Prioridad de Implementación

1. **CRÍTICO (Hacer primero):**
   - Sistema de traducción ES/EN
   - Navegación fija
   - Botón WhatsApp flotante
   - Optimización mobile

2. **ALTA (Hacer segundo):**
   - Demo interactiva
   - Sistema de testimonios
   - Calculadora de precios

3. **MEDIA (Hacer tercero):**
   - Simplificación de código visible
   - Analytics local
   - Comparativa visual mejorada

4. **BAJA (Hacer último):**
   - Exit-intent popup
   - A/B testing
   - Onboarding guiado

## Criterios de Calidad

- ✅ **Performance:** Lighthouse score > 90
- ✅ **Accesibilidad:** WCAG 2.1 AA
- ✅ **Responsive:** Funciona en 320px - 2560px
- ✅ **Offline:** Todo funciona sin internet
- ✅ **SEO:** Meta tags, schema markup
- ✅ **Seguridad:** Sin vulnerabilidades XSS

## Testing Requerido

```bash
# Probar en diferentes dispositivos
- iPhone SE (375px)
- iPad (768px)
- Desktop (1920px)

# Probar sin internet
- Desconectar WiFi
- Recargar página
- Todas las funcionalidades deben trabajar

# Probar navegadores
- Chrome
- Firefox
- Safari
- Edge
```

## Archivos a Modificar/Crear

```
Identidad_AHA/
├── index.html (modificar)
├── css/
│   └── custom.css (crear/modificar)
├── js/
│   ├── translations.js (crear)
│   ├── demo.js (crear)
│   ├── calculator.js (crear)
│   ├── analytics.js (crear)
│   └── main.js (modificar)
└── assets/
    └── images/ (agregar avatares)
```

## Comandos para Ejecutar

```bash
# Servidor local para probar
python -m http.server 8000

# O con Node.js
npx serve .

# Abrir en navegador
http://localhost:8000
```

---

# CHECKLIST FINAL

Antes de considerar completada cada fase, verificar:

- [ ] Código funciona sin errores en consola
- [ ] Responsive en móvil, tablet, desktop
- [ ] Accesible con teclado (Tab, Enter, Esc)
- [ ] Funciona offline completamente
- [ ] Sin dependencias externas pesadas
- [ ] Traducciones completas ES/EN
- [ ] Performance óptimo (< 3s carga)
- [ ] SEO básico (meta tags, titles)
- [ ] Analytics trackeando correctamente
- [ ] Todos los CTAs funcionan
- [ ] WhatsApp integration funciona
- [ ] Demo interactiva genera PDF
- [ ] Calculadora calcula correctamente
- [ ] Testimonios cargan y navegan

---

**NOTA FINAL:** Este prompt está diseñado para ser ejecutado por OpenCode de forma incremental. Implementa una fase a la vez, prueba exhaustivamente, y luego pasa a la siguiente. No intentes hacer todo de una vez.
```

---

## 📝 Cómo Usar Este Prompt

1. **Copia todo el contenido** del bloque de código anterior
2. **Pega en OpenCode** como contexto inicial
3. **Especifica qué fase implementar** primero:
   ```
   "Implementa la FASE 1.1: Sistema de Traducción ES/EN"
   ```
4. **Prueba exhaustivamente** antes de pasar a la siguiente fase
5. **Itera** si hay errores o mejoras necesarias

## 💡 Tips Adicionales

- **Sé específico:** Si algo no funciona, describe el error exacto
- **Pide explicaciones:** "Explícame cómo funciona este código"
- **Solicita variaciones:** "Dame 3 alternativas para este componente"
- **Pide tests:** "¿Cómo puedo probar que esto funciona correctamente?"
