<template>
  <Layout>

       <section class="section">
                <div class="section__inner grid grid__header-section">
                    <div class="tile loading v-3 h-3" ></div>
                    <div class="tile loading"></div>
                    <div class="tile loading"></div>
                    <div class="tile loading"></div>
                </div>
            </section>

             <section class="section">
                <header class="section__header">
                    <h2>What I bluit</h2>
                    <p class="desc">
                        I recently started to express myself trough writing. I have always liked to share knowledge and to teach, Medium is a place where I write about daily thoughts but also build courses.
                    </p>
                </header>
                <div class="section__inner grid grid__header-section">
                    <div class="tile loading v-3 h-3" ></div>
                    <div class="tile loading"></div>
                    <div class="tile loading v-2"></div>
                   
                </div>
            </section>

             <section class="section">
                <header class="section__header">
                    <h2>Posts</h2>
                    <p class="desc">
                        I recently started to express myself trough writing. I have always liked to share knowledge and to teach, Medium is a place where I write about daily thoughts but also build courses.
                    </p>
                </header>
                <div class="section__inner grid grid__list_3">
                    <div v-for="project in $page.projects.edges" :key="project.id" class="tile  v-1 h-1" :style="{
                        'background-image': `url('${project.node.thumbnail.src}')`, 
                        }
                        " style="background-repeat:no-repeat;background-size:cover;">
                    </div>
                
                   
                   
                </div>
            </section>

  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost {
        edges {
            node {
                id
                date (format: "YYYY")
                title
                categories
                thumbnail (width: 200, height: 200,quality: 90)
                path
            }
        }
    },
    journals: allJournalPost (perPage: 4) {
        edges {
        node {
            id
            path
            title
        }
        }
    }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"


export default {
    components: {
        Hero,
        ProjectsGrid,
        LatestJournals
    },
    mounted() {

    },
  
}
</script>
