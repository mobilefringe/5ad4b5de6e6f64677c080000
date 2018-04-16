<template>
	<div class="row page_content" v-if="dataLoaded">
	    <main>
            <section class="slides"> 
              
              <section class="slides-nav">
                <nav class="slides-nav__nav">
                  <button class="slides-nav__prev js-prev" ref="js_prev" @click="prevSlide">Prev</button>
                  <button class="slides-nav__next js-next" ref="js_next" @click="nextSlide">Next</button>
                </nav>
              </section>
            
              <section class="slide is-active">
                <div class="slide__content">
                  <figure class="slide__figure"><div class="slide__img" style="background-image: url(https://source.unsplash.com/nfTA8pdaq9A/2000x1100)"></div></figure>
                  <header class="slide__header">
                    <h2 class="slide__title">
                      <span class="title-line"><span>Click, Key</span></span>
                      <span class="title-line"><span>Or Scroll Fool</span></span>
                    </h2>
                  </header>
                </div>
              </section>
            
              <section class="slide">
                <div class="slide__content">
                  <figure class="slide__figure"><div class="slide__img" style="background-image: url(https://source.unsplash.com/okmtVMuBzkQ/2000x1100)"></div></figure>
                  <header class="slide__header">
                    <h2 class="slide__title">
                      <span class="title-line"><span>Slide Two</span></span>
                      <span class="title-line"><span>Dood Mood</span></span>
                    </h2>
                  </header>
                </div>
              </section>
            
              <section class="slide">
                <div class="slide__content">
                  <figure class="slide__figure"><div class="slide__img" style="background-image: url(https://source.unsplash.com/WuQME0I_oZA/2000x1100)"></div></figure>
                  <header class="slide__header">
                    <h2 class="slide__title">
                      <span class="title-line"><span>This Right</span></span>
                      <span class="title-line"><span>Here Makes Three</span></span>
                    </h2>
                  </header>
                </div>
              </section>
            
              <section class="slide">
                <div class="slide__content">
                  <figure class="slide__figure"><div class="slide__img" style="background-image: url(https://source.unsplash.com/NsWcRlBT_74/2000x1100)"></div></figure>
                  <header class="slide__header">
                    <h2 class="slide__title">
                      <span class="title-line"><span>How Now</span></span>
                      <span class="title-line"><span>Part Four More</span></span>
                    </h2>
                  </header>
                </div>
              </section>
            </section>
        </main>
    </div>
</template>

<script>
    define(["Vue", "jquery"], function(Vue, $) {
        return Vue.component("slice-slider", {
            template: template, // the variable template will be injected
            data: function() {
                return {
                    options 
                }
            },
            created () {
                
            },
            mounted () {
               
            },
            watch : {
            },
            computed: {
            },
            methods: {
                init () {
                    s = this.settings;
                },
                prevSlide () {
                    // If on first slide, loop to last
                      if (s.currentSlideIndex <= 0) {
                        s.currentSlideIndex = s.numSlides;
                      }
                      s.currentSlideIndex--;
                      
                      this.showSlide();
                },
                nextSlide () {
                    s.currentSlideIndex++;
                   
                      // If on last slide, loop to first
                      if (s.currentSlideIndex >= s.numSlides) { 
                        s.currentSlideIndex = 0;
                      }
                 
                      this.showSlide();
                      console.log("sliding to next");
                },
                showSlide () {
                    // reset
                      s.delta = 0;
                      // Bail if we're already sliding
                      if ($('body').hasClass('is-sliding')){
                        return;
                      }
                      // Loop through our slides
                      s.slides.each(function(i, slide) {
                
                        // Toggle the is-active class to show slide
                        $(slide).toggleClass('is-active', (i === s.currentSlideIndex)); 
                        $(slide).toggleClass('is-prev', (i === s.currentSlideIndex - 1)); 
                        $(slide).toggleClass('is-next', (i === s.currentSlideIndex + 1)); 
                        
                        // Add and remove is-sliding class
                        $('body').addClass('is-sliding');
                
                        setTimeout(function(){
                            $('body').removeClass('is-sliding');
                        }, 1000);
                      });
                }
            }
        })
    });
    
</script>
