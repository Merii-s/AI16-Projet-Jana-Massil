<script setup>  
import { ref } from 'vue'; 
const listItems = ref([]); 

async function getData() {
    const res = await fetch("http://localhost:3001/api/users");
    const finalRes = await res.json();
    listItems.value = finalRes; 
    console.log(finalRes)
}
getData();
</script>
<template>
    <div>
        <h1> Liste des utilisateurs </h1>
        <table border="1">
            <thead>
            <tr>                     
                <th scope="col">Nom</th>                     
                <th scope="col">Prenom</th>                    
                <th scope="col">Email</th>                 
            </tr>             
        </thead>             
        <tbody>                 
            <tr v-for="item in listItems">                      
                <td>{{ item.nom }}</td>                     
                <td>{{ item.prenom }}</td>                     
                <td>{{ item.email }}</td>                  
            </tr>             
        </tbody>         
    </table>     
</div> 
</template>

