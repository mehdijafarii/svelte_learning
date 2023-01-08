<script>
  let showModel = true;
  let isPromo = false;
</script>

{#if showModel}
  <div class="backdrop" class:promo={isPromo}>
    <div class="modal">
      <p>Sign up for offers!!</p>
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgb(0, 0, 0, 0.8);
  }

  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10px auto;
    text-align: center;
    background: white;
  }

  .promo .modal {
    background: crimson;
    color: white;
  }
</style>
