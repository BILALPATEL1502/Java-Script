<template>
    <div class="login-wrapper">
        <div class="login-card">
            <h1>Welcome Back</h1>

            <div class="input-group">
                <label>Username</label>
                <input type="text" v-model="email" placeholder="Enter username" />
            </div>

            <div class="input-group">
                <label>Password</label>
                <input type="password" v-model="password" placeholder="Enter password" />
            </div>

            <div v-if="errorMessage" class="error-alert">
                {{ errorMessage }}
            </div>

            <button @click="handleLogin" :disabled="isLoading">
                {{ isLoading ? 'Processing...' : 'Sign In' }}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            email: '',
            password: '',
            isLoading: '',
            login: '',
            errorMessage:''
        }
    },
methods: {
            async handleLogin() {
                // Reset error
                this.errorMessage = '';
                
                // Basic validation variable check
                if (!this.email || !this.password) {
                    this.errorMessage = "Please fill in all fields.";
                    return;
                }

                // Start loading state
                this.isLoading = true;

                try {
                    // Simulate an API call (wait 2 seconds)
                    await new Promise(resolve => setTimeout(resolve, 2000));

                    // Fake success logic
                    if (this.email === "admin" && this.password === "1234") {
                        alert("Login Successful!");
                    } else {
                        throw new Error("Invalid credentials.");
                    }
                } catch (error) {
                    this.errorMessage = error.message;
                } finally {
                    // Stop loading state
                    this.isLoading = false;
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>