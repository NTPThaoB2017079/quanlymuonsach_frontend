<template>
    <div class="favorites">
        <h1>Sách Yêu Thích</h1>
        <div v-if="books.length === 0">Bạn chưa yêu thích quyển sách nào.</div>
        <div class="container" v-else>
            <table class="table">
                    <thead>
                        <tr>
                            <th>
                                STT    
                            </th>
                            <th>
                                Ảnh Sách
                            </th>
                            <th>
                                Tên Sách
                            </th>
                            <th>
                                Tác Giả
                            </th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(book, index) in books" :key="index">
                            <th>
                                {{ index + 1 }}
                            </th>
                            <th>
                                <img width="150px" height="200px" class="img" :src="'http://localhost:3000/uploads/' + book.image" alt="Book Image" />
                            </th>
                            <th>{{ book.name }}</th>
                            <th>{{ book.author }}</th>
                        </tr>
                    </tbody>
                </table>
        </div>
    </div>
</template>

<script>
import UserService from "../services/users.service";
import BookService from "../services/books.service";
export default {
    data() {
        return {
            books: [],
        };
    },
    created() {
        this.retrieveFavorites();
    },
    methods: {
        async retrieveFavorites() {
            try {
                const user = localStorage.getItem("user");
                if (user) {
                    const userData = JSON.parse(user);
                    const favoriteBookIds = userData.favorite; // Assuming these are product IDs
                    const favoriteBooks = await Promise.all(
                        favoriteBookIds.map(async (bookId) => {
                            return await BookService.getBookById(bookId);
                        })
                    );
                    console.log(this.books);
                    this.books = favoriteBooks.filter(Boolean);
                }
            } catch (error) {
                console.error("Error retrieving favorites:", error);
            }
        },
    },
};
</script>

<style>
 h1 {
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: 'Times New Roman', serif;
    color: #FF204E;
    font-weight: bold;
}

</style>