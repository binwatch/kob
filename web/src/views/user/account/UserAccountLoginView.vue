<template>
    <ContentField>
        <div class="row justify-content-md-center">
            <div class="col-3">
                <form @submit.prevent="login">
                    <div class="mb-3">
                        <label for="username" class="form-label">username</label>
                        <input v-model="username" type="text" class="form-control" id="username" placeholder="please enter username">
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">password</label>
                        <input v-model="password" type="password" class="form-control" id="password" placeholder="please enter password">
                    </div>
                    <div class="error-message">{{ error_message }}</div>
                    <button type="submit" class="btn btn-primary">submit</button>
                </form>
            </div>
        </div>
    </ContentField>
</template>

<script>
import { ref } from "vue";
import { useStore } from "vuex";
import ContentField from "../../../components/ContentField.vue";
import router from '../../../router/index'

export default {
    components: {
        ContentField
    },
    setup() {
        const store = useStore();
        let username = ref('');
        let password = ref('');
        let error_message = ref('');

        const login = () => {
            error_message.value = "";
            store.dispatch("login", {
                username: username.value,
                password: password.value,
                success() {
                    store.dispatch("getinfo", {
                        success() {
                            router.push({ name: 'home' });
                            console.log(store.state.user);
                        }
                    });
                    router.push({ name: 'home' });
                },
                error() {
                    error_message.value = "wrong username or password";
                }
            });
        }
        return {
            username,
            password,
            error_message,
            login,
        }
    }
}
</script>

<style scoped>
div.error-message {
    color: red;
}
button {
    width: 100%;
}
</style>