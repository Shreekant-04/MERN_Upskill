
<!DOCTYPE html>
<html>

<head>
    <title>Table Data Searching Using JavaScript</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
</head>
<body>

    <div class="container mt-5 pb-5 pt-5 " style="background-color: rgb(217, 235, 250);border-radius: 20px;">

        <div class="row ">
            <div class="offset-md-3 col-md-6  ">
                <input type="search" class="form-control" id="search" placeholder="Live Searching.....">
            </div>
        </div>

        <h3 id="error" class="text-center mt-3"></h3>

        <div class="row ">
            <div class="offset-md-1 col-md-10 ">

                <table class="table table-bordered border-primary table-hover mt-5 text-capitalize" id="mytable">
                </table>

            </div>
        </div>
    </div>

    <script>
        var array = [
    {
        id: "1",
        name: "farhan",
        country: "pakistan",
        city: "karachi"
    },
    {
        id: "2",
        name: "ali",
        country: "india",
        city: "mumbai"
    },
    {
        id: "3",
        name: "subhan",
        country: "afghanistan",
        city: "kabul"
    },
    {
        id: "4",
        name: "john",
        country: "europe",
        city: "england"
    },
    {
        id: "5",
        name: "smith",
        country: "russia",
        city: "moscow"
    }
]

function showtable(curarray) {
    document.getElementById("mytable").innerHTML = `
    <tr class="bg-primary text-white fw-bold">
                <td>ID</td>
                <td>Name</td>
                <td>Country</td>
                <td>City</td>
            </tr> ` ;

    if (curarray == "") {
        document.getElementById("error").innerHTML = `<span class='text-danger '>Not Found!</span>`;
    }
    else {

        document.getElementById("error").innerHTML = "";

        for (var i = 0; i < curarray.length; i++) {
            document.getElementById("mytable").innerHTML += ` 
              <tr > <td>${curarray[i].id}</td> <td>${curarray[i].name}</td> 
                <td>${curarray[i].country}</td> <td>${curarray[i].city}</td> </tr>`;
        }
    }
}


showtable(array);

var newarray = [];

document.getElementById("search").addEventListener("keyup", function () {
    var search = this.value.toLowerCase();

    newarray = array.filter(function (val) {

        if (val.id.includes(search) || val.name.includes(search) || val.country.includes(search)
            || val.city.includes(search)) {
            var newobj = { id: val.id, name: val.name, country: val.country, city: val.city }
            return newobj;
        }
    });

    showtable(newarray);

});
  
    </script>

</body>

</html>
