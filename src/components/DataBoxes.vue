<template>
 <div class="container">
     <div class="row justify-content-center text-center">
        <div class="col-md-6 py-3">
            <div class="card bg-danger text-white" style="width: 18rem;">
            <div class="card-body">
                <h5 class="card-title">Cases</h5>
                <h6 class="card-subtitle mb-2 ">New: {{stats.NewConfirmed}}</h6> 
                <h6 class="card-subtitle mb-2 ">Total: {{stats.TotalConfirmed}}</h6>
                
  
            </div>
</div>
        </div>
           <div class="col-md-6 py-3">
            <div class="card bg-dark text-white " style="width: 18rem;">
            <div class="card-body">
                <h5 class="card-title">Deaths</h5>
                <h6 class="card-subtitle mb-2">NewDeaths: {{stats.NewDeaths}}</h6>
                
                <h6 class="card-subtitle mb-2">Total Deaths: {{stats.TotalDeaths}}</h6>
             
              
            </div>
</div>
        </div>
     </div>
     
 </div>
</template>
<script>
export default {
    name:'DataBoxes',
    props:['stats'],
}
</script>