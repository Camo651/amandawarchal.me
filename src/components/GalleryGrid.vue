<template>
    <div class="gallery-grid">
        <GalleryItem @showcase="openShowcase"
            v-for="item in getGallery()"
            :key="item.id"
            :id="item.id"
            :src="item.src"
            :title="item.title"
        />
        <Transition name="fade">
            <ShowcaseModal v-if="showcaseId !== null" @close="showcaseId = null" :item="gallery[showcaseId]"/>
        </Transition>
    </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import ShowcaseModal from "./ShowcaseModal.vue";
import GalleryItem from "./GalleryItem.vue";

// gallery item interface
interface GalleryItemType {
    id: number;
    src: string;
    title: string;
    medium: string;
    elements?: ShowcaseElement[];
}
interface ShowcaseElement {
    title?: string;
    text?: string;
    img?: string;
    caption?: string;
}
export default defineComponent({
    name: "GalleryGrid",
    components: {
        ShowcaseModal,
        GalleryItem,
    },
    data() {
        return {
            showcaseId: null as number | null,
            gallery: [
                {
                    src: require("@/assets/images/e/1.jpg"),
                    title: "Joker",
                    medium: "Acrylic on Canvas Board",
                    elements: [
                        {
                            text: "A piece inspired by the release of the movie Joker. Dry-brushing techniques were utilized and layers of coloration were added in order to achieve a realistic skin texture. Similar techniques were used to create the textures of the hair and jacket.",
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/e/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/e/3.jpg"),
                        },
                        {
                            img: require("@/assets/images/e/4.jpg"),
                        }
                    ]
                },
                {
                    src: require("@/assets/images/c/1.jpg"),
                    title: "Cracked Heart",
                    medium: "Watercolor & Acrylic on Paper",
                    elements: [
                        {
                            text: "I was looking to experiment with the idea of having hyper-realistic elements in a piece, but arranging them in a manner that ultimately made their composition unlike anything seen in real life. I have an obsession with adding gold paint to pieces that I enjoy making, and thus I couldn’t resist adding some to the blood dripping from the cracked heart. (Also, the play on the golden blood or ichor of greek gods was a little easter egg that I thought would bring a fun double-meaning to the piece)"
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/c/6.jpg"),
                        },
                        {
                            img: require("@/assets/images/c/7.jpg"),
                        },
                        {
                            img: require("@/assets/images/c/2.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/o/1.jpg"),
                    title: "Bust of Man",
                    medium: "Watercolor on Paper",
                    elements: [
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/o/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/o/3.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/b/1.jpg"),
                    title: "Reflection",
                    medium: "Watercolor & Acrylic on Paper",
                    elements: [
                        {
                            text: "For this piece, I was looking to explore some of the differences in working with watercolor and acrylic paints, as well as some of the differences in painting in grayscale or in full color. As a result, I sketched the same girl twice and painted one rendition of her in full color using the watercolor, and the other in grayscale using acrylic paint. The backgrounds on either side of the painting were filled in with the opposite medium to really play on that idea of comparison and juxtaposition."
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/b/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/b/3.jpg"),
                        },
                    ]
                },

                {
                    src: require("@/assets/images/d/1.jpg"),
                    title: "Self Empathy",
                    medium: "Watercolor on Paper",
                    elements: [
                        {
                            text: "This piece was inspired by the premise of being as kind to yourself as you are to others, and as a result, I decided that I wanted to create an image where I was literally giving that kindness to myself."
                        },
                        {
                            text: "In order to make this piece, I first needed to come up with a way to obtain a reference of me hugging myself -which is not quite as easy as capturing a reference of two separate people hugging-, so that is where I started. I enlisted the help of two of my friends so that we could take reference shots in which I was both the person on the outside of the embrace, and also the person within it. Once I had a picture where I was present in both parts of the hug, I then grafted the two images together digitally using Photopea so that I could begin making a sketch, and once that was done I was able to use my grafted photo as a reference to complete the remainder of the painting process!"
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/d/3.jpg"),
                        },
                        {
                            img: require("@/assets/images/d/6.jpg"),
                        },
                        {
                            img: require("@/assets/images/d/4.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/f/1.jpg"),
                    title: "Lemon",
                    medium: "Chalk Pastel on Paper",
                    elements: [
                        {
                            text: "A study of a lemon, drawn from life."
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/f/2.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/g/1.jpg"),
                    title: "Drapery",
                    medium: "Chalk Pastel on Paper",
                    elements: [
                        {
                            text: "A study of drapery, drawn from life."
                        },
                    ]
                },
                {
                    src: require("@/assets/images/h/1.jpg"),
                    title: "Spring (Odilon Redon)",
                    medium: "Graphite on Paper",
                    elements: [
                        {
                            text: "This piece is more like a study of Odilon Redon’s piece Spring, as I had viewed it at my local art museum and was instructed by my art professor to use the grid method to make a black and white rendition of the piece in an attempt to understand its composition a bit better. From here, I would go on to create my own version of Spring."
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/h/3.jpg"),
                            caption: "Odilon Redon's Original Spring",
                        },
                        {
                            img: require("@/assets/images/h/2.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/j/1.jpg"),
                    title: "Spring Reimagined",
                    medium: "Watercolor & Acrylic on Paper",
                    elements: [
                        {
                            text: "Here is where I processed how I might make my own version of Odilon Redon’s Spring. At first I began with four sketches of completely different ways that I might reimagine this piece, but ultimately I decided on the idea of having some more recognizable nature in the piece, as well as the idea of having the woman in the picture actually interacting with that nature as opposed to staring out at the audience."
                        },
                        {
                            text: "In the end, I utilized watercolor and gold acrylic paint to finish off this piece, and made sure to add in some symbolism with the presence of the hummingbirds -which often are an omen that spring is coming-, and the golden orbs around the heads of each bird, indicating that the new season is of high importance."
                        },
                        {
                            title: "Detail shots:",
                        },
                        {
                            img: require("@/assets/images/j/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/j/3.jpg"),
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/j/5.jpg"),
                        },
                        {
                            img: require("@/assets/images/j/4.jpg"),
                        }
                    ]
                },
                {
                    src: require("@/assets/images/i/1.jpg"),
                    title: "Hand Study",
                    medium: "Graphite on Paper",
                    elements: [
                        {
                            text: "A study of my hand, drawn from life.",
                        }
                    ]
                },
                {
                    src: require("@/assets/images/k/1.jpg"),
                    title: "Flowers in Persian Miniature",
                    medium: "Gouache & Tea on Paper",
                    elements: [
                        {
                            text: "This piece was made in the tradition of Persian miniature painting. Such a tradition entails the use of black tea to first stain the paper, a burnishing tool -like a cowry shell or a large glass bead-, and gouache to be added in layers of flood and then extreme linear detail. Once the paper I used for this piece had been stained with two rounds of tea, I then went about burnishing the paper by rubbing a glass bead over it in all directions until the whole page was shiny. Once this round of burnishing was completed, I then set to work flooding each petal and leaf with gouache in the color of my choice. When the flooding stage was completed, I then burnished the entirety of the paper once more before going in with a very small detail brush and making thin lines over each flower and leaf until I had achieved my desired level of detail."
                        },
                        {
                            text: "Although the full tradition of Persian miniature painting has many more specifications involved with its process, I found that it was very intriguing to learn a version of this method of painting and see first-hand how much effort actually goes into making pieces like this."
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/k/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/k/3.jpg"),
                        }
                    ]
                },
                {
                    src: require("@/assets/images/m/1.jpg"),
                    title: "Rabbit in Wonderland",
                    medium: "Walnut Ink on Paper",
                    elements: [
                        {
                            text: "This piece represents an exploration of ink as a medium. I utilized a similar brushstroke technique to that of the detail-work in Persian miniature paintings, and let the ink lead me to this final product."
                        }
                    ]
                },
                {
                    src: require("@/assets/images/l/1.jpg"),
                    title: "The Balloon",
                    medium: "Watercolor & Gouache on Paper",
                    elements: [
                        {
                            text: "This was a commissioned piece in which I utilized watercolor and gouache to depict a hot air balloon flying over a colorful landscape. My favorite aspects about this piece are truly the small details within it, as well as the process by which I ended up building color within this piece, as I think that the vibrant color-scheme that resulted from that process is unlike anything else I have made before."
                        },
                        {
                            title: "Detail shots:",
                        },
                        {
                            img: require("@/assets/images/l/10.jpg"),
                        },
                        {
                            img: require("@/assets/images/l/9.jpg"),
                        },
                        {
                            img: require("@/assets/images/l/11.jpg"),
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/l/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/l/4.jpg"),
                        },
                        {
                            img: require("@/assets/images/l/5.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/a/1.jpg"),
                    title: "Soil Microbe Study",
                    medium: "Graphite on Paper",
                    elements: [
                        {
                            text: "This piece was inspired by the process of searching for potential antibiotic-producing microbes in a soil sample that I collected for a biology lab that I am taking. Within this piece, I featured some sketches of the interesting colony morphology that I have witnessed on the agar plates that I have been making in the course, as well as a plethora of the tools and vessels that I have been using in the process of making these plates. My favorite colony that I have witnessed thus far on any plate has been these small, white, flower-shaped colonies that are featured towards the center of the piece."
                        },
                        {
                            title: "Detail shots:",
                        },
                        {
                            img: require("@/assets/images/a/6.jpg"),
                        },
                        {
                            img: require("@/assets/images/a/7.jpg"),
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/a/2.jpg"),
                        },
                        {
                            img: require("@/assets/images/a/3.jpg"),
                        },
                    ]
                },
                {
                    src: require("@/assets/images/n/1.jpg"),
                    title: "Types of Cyanobacteria",
                    medium: "Watercolor on Paper",
                    elements: [
                        {
                            text: "For a project in my Fundamentals of Microbiology course, I decided to focus on learning about Cyanobacteria, and as a result, I wanted to create a small piece that would allow me to showcase the different kinds of cyanobacteria that can be seen under a microscope."
                        },
                        {
                            title: "Process photos:",
                        },
                        {
                            img: require("@/assets/images/n/3.jpg"),
                        },
                        {
                            img: require("@/assets/images/n/4.jpg"),
                        },
                    ]
                }
            ] as GalleryItemType[],
        };
    },
    methods: {
        openShowcase(id: number) {
            this.showcaseId = id;
        },
        getGallery(): GalleryItemType[] {
            for (let i = 0; i < this.gallery.length; i++) {
                this.gallery[i].id = i;
            }
            return this.gallery;
        },
        getMainStyle() {
            // prevent scroll when modal is open
            document.body.style.overflow = this.showcaseId !== null ? "hidden" : "";
        },
    },
    watch: {
        showcaseId() {
            this.getMainStyle();
        },
    },
});
</script>
<style lang="scss">
    .gallery-grid {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-evenly;
        align-items: flex-start;
        gap: 10px;
        width: 100%;
    }

    .fade-enter-active, .fade-leave-active {
        transition: all 0.2s;
    }
    .fade-enter-from, .fade-leave-to {
        opacity: 0;
    }
    .fade-enter-to, .fade-leave {
        opacity: 1;
    }
    
</style>