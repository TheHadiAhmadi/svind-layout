<script>
import Footer from '$lib/components/Footer.svelte';
import Header from '$lib/components/Header.svelte';

	import Page from '$lib/components/Page.svelte';
	import PageBody from '$lib/components/PageBody.svelte';
import Sidebar from '$lib/components/Sidebar.svelte';
import { Checkbox, Radio } from '@svind/svelte';

    let hasHeader = false, hasSidebar = false, hasFooter = false
    let headerInBody = false;
    let footerInBody = false;

    let headerFixed = false;
    let sidebarFixed = false;
    let footerFixed = false;

</script>

<Page>
    {#if hasSidebar}
    <Sidebar open={false} fixed={sidebarFixed}>
        sidebar
    </Sidebar>
    {/if}
    
    {#if hasHeader && !headerInBody}
    <Header fixed={headerFixed}>
        header
    </Header>
    <Header fixed={headerFixed}>
        header
    </Header>
    {/if}
    <PageBody>
    {#if hasHeader && headerInBody}
    <Header fixed={headerFixed}>
        header
    </Header>
    {/if}
    <div>


        <Checkbox bind:value={hasHeader}>
            hasHeader
        </Checkbox>
        <Checkbox bind:value={hasSidebar}>
            hasSidebar
        </Checkbox>
        <Checkbox bind:value={hasFooter}>
            hasFooter
        </Checkbox>

        <Checkbox bind:value={headerFixed}>
            Header Fixed
        </Checkbox>
        <Checkbox bind:value={footerFixed}>
            footer Fixed
        </Checkbox>
        <Checkbox bind:value={sidebarFixed}>
            sidebar Fixed
        </Checkbox>
        
        <Checkbox bind:value={headerInBody}>
            Header in body
        </Checkbox>

        <Checkbox bind:value={footerInBody}>
            Footer in body
        </Checkbox>

        <br>
        <br>
        <br>
        <br>
        <br>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <br><br><br><br><br><br><br><br><br><br>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <br><br><br><br><br><br><br><br><br><br>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <br><br><br><br><br><br><br><br><br><br>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    
       <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    <br><br><br><br><br><br><br><br><br><br>
    <hr>
    <div>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus at fugit voluptates esse
        vitae odit architecto culpa illum id repellendus distinctio ducimus tempora ipsa, debitis
        soluta! Libero quasi quaerat nam.
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique rem, repellat soluta odio
            dolorum asperiores sequi, veniam illo impedit ad corrupti, debitis voluptate minima
            distinctio quos hic corporis doloribus reiciendis.
        </p>
        <br />
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis rem nobis, eligendi eos
            vitae dolorem ipsa voluptatum quo natus aut a repudiandae, fuga numquam laborum corporis
            veniam vero excepturi explicabo.
        </p>
    </div>
    {#if hasFooter && footerInBody}
        <Footer fixed={footerFixed}>
            footer
        </Footer>
    {/if}
</PageBody>

{#if hasFooter && !footerInBody}
<Footer fixed={footerFixed}>
    footer
</Footer>
{/if}
</Page>
