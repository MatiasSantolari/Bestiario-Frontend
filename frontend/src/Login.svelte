<script>
    import { useForm, validators, HintGroup, Hint, email, required } from "../node_modules/svelte-use-form";
    const form = useForm();
    let showModal = true;
    let isPromo = true;
</script>
  
    {#if showModal}
        <div class="backdrop" class:promo={isPromo}>
            <div class="modale"> <!--no le puse modal porque me da error con bootstrap creo-->
                <form use:form>
                    <h1>Login</h1>
                    <input type="email" name="email" use:validators={[required, email]} />
                    <HintGroup for="email">
                        <Hint on="required">This is a mandatory field</Hint>
                        <Hint on="email" hideWhenRequired>Email is not valid</Hint>
                    </HintGroup>

                    <input type="password" name="password" use:validators={[required]} />
                    <Hint for="password" on="required">This is a mandatory field</Hint>
                    <br>
                    <button disabled={!$form.valid}>Login</button>
                </form>
            </div>
        </div>
    {/if}
  
<style>
    :global(.touched:invalid) {
		border-color: red;
		outline-color: red;
	}
    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8);
    }
    .modale{
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
    .promo .modale{
        background: rgb(4, 124, 20);
        color: white;
    }
</style>