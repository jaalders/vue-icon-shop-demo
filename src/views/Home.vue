<script setup>
  import ProductCard from '@/components/ProductCard.vue'
</script>

<script>
  export default {
    name: "Home",
    props: ['inventory', 'addToCart']
  }
</script>

<template>
  <main>
    <div class="container-fluid overflow-hidden hero pb-4">
      <div class="row">
        <div class="col-2"></div>
        <div class="col-8">
          <br>
          <h2 class="text-center">Welcome to IconiCoaster - Where Your Everyday Icons Become Artful Coasters!</h2>
          <br>
          <p class="text-left">At IconiCoaster, we're all about turning the ordinary into extraordinary. We believe that even the icons we use every day on our devices can be transformed into functional and beautiful works of art. Say goodbye to boring coasters and hello to a unique and personalized way to protect your surfaces with our stunning coasters made from your favorite icons.</p>
          <p class="text-left">Why settle for generic coasters when you can showcase your personal style with coasters that reflect your digital world? Whether it's the classic smiley face emoji that always brightens your day, the retro floppy disk that brings back memories of simpler times, or the trendy avocado emoji that represents your love for all things foodie - we have a coaster that's perfect for you!</p>
          <p class="text-left">Our coasters are meticulously crafted using high-quality materials to ensure durability and longevity. Each coaster is made with precision and attention to detail, capturing the essence of the icon that inspires it. The result? A functional piece of art that adds a touch of personality and flair to any space.</p>
          <p class="text-left">At IconiCoaster, we are committed to sustainability and eco-friendliness. We use eco-friendly materials and practices in our production process to minimize our environmental impact. Our coasters are also designed to be reusable, reducing waste and promoting a greener lifestyle.</p>
          <p class="text-left">Ready to elevate your coaster game? Join us at IconiCoaster and discover the joy of functional art. Whether it's for your own home or as a thoughtful gift for a loved one, our coasters are sure to make a statement. Start creating your custom coaster today and let your favorite icons take center stage!</p>
        </div>
        <div class="col-2"></div>
      </div>
    </div>
    
    <div class="col-12 mb-5">
    </div>
    
    <div class="col-12 py-3">
      <h2 class="text-center">Here are some of our coasters based upon the most recent purchases.</h2>
    </div>

    <div class="container-fluid">
      <div class="row row-cols-1 row-cols-md-4 g-4">
        <ProductCard 
          v-for="(product, index) in inventory.slice(0, 4)" 
          :key="product.id"
          :index="index"
          :product="product"
          :addToCart="addToCart"
        />
      </div>
    </div>
  </main>
</template>


