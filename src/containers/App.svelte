<script>
  import Header from "./../components/Header.svelte";
  import Main from "./../components/Main.svelte";
  import TimeLine from "./../components/TimeLine.svelte";
  import SideBar from "./../components/SideBar.svelte";
  import { onMount } from "svelte";

  let data = {};
  const Api = 'https://us-central1-pugstagram-co.cloudfunctions.net/data';

  onMount(async () => {
    await fetch(Api)
      .then((dats) => dats.json())
      .then((dats) => {
        data = dats;
      })
  });


</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

  :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
  }

  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>

<Header />
<Main>
  <TimeLine posts={data.posts} />
  <SideBar {...data.user} />
</Main>