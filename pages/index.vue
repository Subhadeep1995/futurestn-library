<template>

<div>
  
  <section class="hero">
    <div class="hero-body">
      <div class="container">
        <h1 class="title">
          FutureStation Library
        </h1>
      </div>
    </div>
  </section>

  <div class="wrapper has-background-light">
    
    <div class="container">


          <div 
          class="tile is-ancestor container is-fluid" 
          v-for="(doc, index) in library"
          :key="index"
          >
      <div class="tile is-vertical is-2">
        <div class="tile">
          
          <div class="tile is-parent">
            <article class="tile has-background-white is-child notification">
              <figure class="image is-200x200">
                <img v-bind:src="doc.fields.imageUrl">
              </figure>
            </article>
          </div>
        </div>
      </div>
      <div class="tile is-parent">
        <article class="is-child notification container is-fluid has-background-white">
          <div class="content">
            <h2>{{doc.fields.title}}</h2>
            <p>{{doc.fields.description}}</p>
            <p><a v-bind:href="doc.fields.fileUrl" class="button is-link">Download</a></p>
            <div class="content">
              <!-- Content -->
            </div>
          </div>
        </article>
      </div>
    </div>

    
    </div>


  </div>
</div>

</template>

<script>
import client from '~/plugins/contentful'

export default {
  asyncData() {
    return client.getEntries({
      content_type: 'library',
    })
    .then(entries => {
      return {library: entries.items};
    })
    .catch(e => console.log(e));
  }
}
</script>

<style>

.wrapper {
  padding-top: 50px;
}
</style>

