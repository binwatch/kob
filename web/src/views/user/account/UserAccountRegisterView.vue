<template>
    <ContentField>
        <div class="row justify-content-md-center">
            <div class="col-3">
                <form>
                    <div class="mb-3">
                        <label for="username" class="form-label">username</label>
                        <input type="text" class="form-control" id="username" placeholder="please enter username">
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">password</label>
                        <input type="password" class="form-control" id="password" placeholder="please enter password">
                    </div>
                    <div class="error-message">wrong password</div>
                    <button type="submit" class="btn btn-primary">submit</button>
                </form>
            </div>
        </div>
    </ContentField>
</template>

<script>
import ContentField from "../../../components/ContentField.vue";
export default {
    components: {
    ContentField
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