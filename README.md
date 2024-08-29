let express = require("express");
let app = express();
let port = 3000;

// E1 - Employees
let employees = [
{name: "Rahul Gupta", department: "HR", salary: 5000},
{name:'Snehal Sharma', department: 'Finance', salary: 6000},
{name:'Priya Singh', department: 'Marketing', salary: 55000},
{name:'Amit Kumar', department: 'IT', salary: 6500}
];

function filterByDepartment(emp, department) {
return emp.department === department;
}

app.get('/employees/department/:department', (req, res) => {
let department = req.params.department;
let result = employees.filter(emp => filterByDepartment(emp, department));
res.json(result);
});

// E2 - Bikes by Mileage
let bikes = [
{make: "Hero", model: 'Splendor', mileage: 80},
{make: "Bajaj", model: 'Pulsar', mileage: 60},
{make: 'TVS', model: "Apacha", mileage: 70}
];

function filterByMileage(bike, minMileage) {
return bike.mileage > minMileage;
}

app.get('/bikes/mileage/:minMileage', (req, res) => {
let minMileage = parseInt(req.params.minMileage);
let result = bikes.filter(bike => filterByMileage(bike, minMileage));
res.json(result);
});

// E3 - Bikes by Make
function filterByMake(bike, make) {
return bike.make.toLowerCase() === make.toLowerCase();
}

app.get('/bikes/make/:make', (req, res) => {
let make = req.params.make;
let result = bikes.filter(bike => filterByMake(bike, make));
res.json(result);
});

// E4 - Songs by Rating
let songs = [
{title: 'Tum Hi Ho', genre: 'Romantic', rating: 4},
{title: 'Senorita', genre: 'Pop', rating: 5},
{title: 'Dil Chahta Hai', genre: "Bollywood", rating: 3}
];

function filterByRating(song, minRating) {
return song.rating === minRating;
}

app.get('/songs/rating/:minRating', (req, res) => {
let minRating = parseInt(req.params.minRating);
let result = songs.filter(song => filterByRating(song, minRating));
res.json(result);
});

// E5 - Songs by Genre
function filterByGenre(song, genre) {
return song.genre.toLowerCase() === genre.toLowerCase();
}

app.get('/songs/genre/:genre', (req, res) => {
let genre = req.params.genre;
let result = songs.filter(song => filterByGenre(song, genre));
res.json(result);
});

// E6 - Tasks by Status
let tasks = [
{taskId: 1, taskName: "Prepare Presentation", status: "pending"},
{taskId: 2, taskName: "Attend Meeting", status: "in-progress"},
{taskId: 3, taskName: "Submit Report", status: "completed"}
];

function filterByStatus(task, status) {
return task.status === status;
}

app.get('/tasks/status/:status', (req, res) => {
console.log(`Received request for status: ${req.params.status}`);
let status = req.params.status;
let result = tasks.filter(task => filterByStatus(task, status));
res.json(result);
});

// Start the Server
app.listen(port, () => {
console.log(`Server is running on http://localhost:${port}`);
});
