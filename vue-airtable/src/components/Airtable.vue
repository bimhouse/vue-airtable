<template>
    <p>Airtable Test Things</p>
</template>

<style scoped>
</style>

<script>
import Airtable from "airtable";

var base = new Airtable({apiKey: 'patYOL27zAdbqZ21x.51f201a55c8563f8503b4a73bbac47c62ee6026c43daecad1486fe4247d8829f'}).base('appLf2zoj9g8fwpFo');

base('Blog').select({
    // Selecting the first 3 records in Data:
    maxRecords: 10,
    view: "Data"
}).eachPage(function page(records, fetchNextPage) {
    // This function (`page`) will get called for each page of records.

    records.forEach(function(record) {
        console.log('Retrieved', record.get('BlogPostName'));
    });

    // To fetch the next page of records, call `fetchNextPage`.
    // If there are more records, `page` will get called again.
    // If there are no more records, `done` will get called.
    fetchNextPage();

}, function done(err) {
    if (err) { console.error(err); return; }
});
</script>