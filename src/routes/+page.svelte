<script lang="ts">
    let tituloDoJogo : string = "Jogo da Digitação"
</script>

<header>
    <h1>
        {tituloDoJogo}
    </h1>
</header>

<div class="cards">
    <div class="card">
        <img class="sobre" src="/images/capa.png" alt="ninja"/>
        <a class="link" href="/jogar">Jogar</a>
    </div>
    <div class="card">
        <img class="sobre" src="/images/capa.png" alt="ninja"/>
        <a class="link" href="/sobre">Sobre</a>
    </div>
</div>


<style scoped>

header {
    padding: 1rem;
}

h1 {
    font-size: 2rem;
    font-weight: 700;
    text-align: center;
    color: rgb(235, 235, 235);
}

.cards {
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.card {
    width: 30rem;
    display: flex;
    background-color: #6b6868;
    border-radius: 5px;
    padding: 1rem;
    margin: 1rem;
    text-align: center;
    align-items: center;
}

.card img {
    width: 10rem;
    margin-left: 0;
}

.card a {
    margin-left: 5rem;
}

.link {
    text-decoration: none;
    color: rgb(255, 255, 255);
    font-size: 1.5rem;
    font-weight: 700;
}

</style>