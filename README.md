const express = require('express');
const axios = require('axios');
const cors = require('cors');

const app = express();
const port = process.env.PORT || 3000;

app.use(cors());

app.get('/', async (req, res) => {
    try {
        const response = await axios.get('https://script.google.com/macros/s/AKfycbwn_n1DE8n3HkRNEaDwcmjQW7lvBsEhNnfWd0my4xs/dev');
        res.send(response.data);
    } catch (error) {
        console.error(error);
        res.status(500).send('Error fetching data');
    }
});

app.listen(port, () => {
    console.log(`Server listening on port ${port}`);
});
