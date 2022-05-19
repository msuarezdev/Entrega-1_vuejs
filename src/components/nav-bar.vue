<template>
    <div>
        <b-navbar toggleable='lg' type="dark" variant="success">
            <b-navbar-brand @click="goHome" href="#">
                <b-icon-brightness-fill-high></b-icon-brightness-fill-high>
            Ecommerce            
            </b-navbar-brand>
            <b-navbar-toogle target="nav-collapse"></b-navbar-toogle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav class="ml-auto">
                    <b-nav-item @click="gotocart" active> Carrito </b-nav-item>

                    <b-navbar-item-dropdown right>
                        <template v-slot:button-content>
                            <em>admin</em>
                        </template>
                        <b-dropdown-item v-b-modal.modal-1>sign in</b-dropdown-item>
                    </b-navbar-item-dropdown>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>

        <div>
            <b-modal hide-footer ref="my-modal" id="modal-1" title="admin">
                <b-form @submit="onSumbit">
                    <b-form-group
                        id= "input-group-1"
                        label="user:"
                        label-for= "input-1"
                    >
                        <b-form-input
                        id="input-1"
                        v-model="form.user"
                        type="text"
                        required
                        placeholder="Ingresar usuario">
                        </b-form-input>
                    </b-form-group>

                                        <b-form-group
                        id= "input-group-2"
                        label="Password:"
                        label-for= "input-2"
                    >
                        <b-form-input
                        id="input-2"
                        v-model="form.pass"
                        type="password"
                        required
                        placeholder="Ingresar contraseña">
                        </b-form-input>
                    </b-form-group>

                    <b-button type="sumbit" block variant="primary"> enviar </b-button>
                </b-form>
            </b-modal>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return{
            cart: '',
            form:{
                user:'',
                pass:''
            } 
        }
    },
    created(){
        if(JSON.parse(localStorage.getItem('products'))){
            this.cart = JSON.parse(localStorage.getItem('products'))
        }else{
            return
        }
    },
    methods:{
        gotocar(){
            
        },
        goHome(){

        },
        onSubmit(e){
            e.preventDefault();
            if(this.form.user=='admin' && this.form.pass=='123456'){
                this.$refs['my-modal'].hide()
                //this.$router.push(/admin)
                localStorage.setItem('admin',JSON.stringify('true'))
            }else{
                return false;
            }
        }
    }
}
</script>

<style>

</style>