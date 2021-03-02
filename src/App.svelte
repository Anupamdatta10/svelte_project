<script>
  import HeaderData from "./header.svelte";

  let color;
  let new_name = "";
  let new_age = "";
  let update_name = "";
  let update_age = "";
  let update_id=""	
  export let name;
  var fun = () => {
    alert("hello from " + name);
    name = "hululo";
  };
  function handelinput(e) {
    color = e.target.value;
  }
  // $:console.log(color); reactive statement

  let people = [
    { name: "anupam", age: "26", id: 1 },
    { name: "rana", age: "26", id: 2 },
    { name: "utshab", age: "26", id: 3 },
    { name: "chandan", age: "16", id: 4 },
  ];
  function del(id) {
    people = people.filter((person) => id != person.id);
  }
  function update_table() {
    let i = people.findIndex((obj => obj.id == update_id));
        people[i]["name"] = update_name;
        people[i]["age"] = update_age;
      
	
  }
  function add_data() {
    let id;

    if (people.length == 0) {
      id = 1;
    } else {
      id = people[people.length - 1]["id"] + 1;
    }

    people = people.concat({ name: new_name, age: new_age, id: id });
    new_name = "";
    new_age = "";
  }
</script>

<HeaderData message="this is test" />

<main>
  <h1>Data base </h1>
  

  {#each people as person (person.id)}
    <div class=" c border1">
      <div class="data">{person.name}</div>
      <div class="data">{person.age}</div>
      {#if person.age > 18}
        <div class="data">adult</div>
      {:else}
        <div class="data">not adult</div>
      {/if}
      <button
        class="btn btn-danger"
        on:click={() => {
          del(person.id);
        }}><i class="fa fa-trash" aria-hidden="true" /> Delete</button
      >
      <button
        type="button"
        class="fleft btn btn-success"
        data-target="#exampleModalCenterupdate"
        data-toggle="modal"
        on:click={() => {
          update_name = person.name;
          update_age = person.age;
          update_id=person.id;
        }}><i class="fa fa-pencil-square-o" aria-hidden="true"></i> Update</button
      >
    </div>
  {:else}
    <div class="c">there is no data</div>
  {/each}
  <button
    type="button"
    class="btn btn-primary c"
    data-toggle="modal"
    data-target="#exampleModalCenter"
  ><i class="fa fa-plus" aria-hidden="true"></i>
    Add data
  </button>

  <!--update modal-->

  <div
    class="modal fade"
    id="exampleModalCenterupdate"
    tabindex="-1"
    role="dialog"
    aria-labelledby="exampleModalCenterTitle"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLongTitleupdate">
            update data in table
          </h5>
          <button
            type="button"
            class="close"
            data-dismiss="modal"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <div class="form-group">
            <label for="input_name" class="col-form-label">name</label>
            <input
              class="form-control"
              id="update_name"
              type="text"
              bind:value={update_name}
            />
          </div>
          <div class="form-group">
            <label for="input_age" class="col-form-label">age</label>
            <input
              class="form-control"
              id="update_age"
              type="text"
              bind:value={update_age}
            />
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-dismiss="modal"
            >Close</button
          >
          <button type="button" class="btn btn-primary" data-dismiss="modal"
		  on:click={update_table}
            >Save changes</button
          >
        </div>
      </div>
    </div>
  </div>
  <!-- Modal -->
  <div
    class="modal fade"
    id="exampleModalCenter"
    tabindex="-1"
    role="dialog"
    aria-labelledby="exampleModalCenterTitle"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLongTitle">
            Add data in table
          </h5>
          <button
            type="button"
            class="close"
            data-dismiss="modal"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <div class="form-group">
            <label for="input_name" class="col-form-label">name</label>
            <input
              class="form-control"
              id="input_name"
              type="text"
              bind:value={new_name}
            />
          </div>
          <div class="form-group">
            <label for="input_age" class="col-form-label">age</label>
            <input
              class="form-control"
              id="input_age"
              type="text"
              bind:value={new_age}
            />
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-dismiss="modal"
            >Close</button
          >
          <button
            type="button"
            class="btn btn-primary"
            data-dismiss="modal"
            on:click={add_data}>Add</button
          >
        </div>
      </div>
    </div>
  </div>
</main>

<style>
  h1 {
    text-align: center;
    color: rgb(207, 92, 38);
  }
  .c {
    display: block;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
    padding: 10px;
  }
  .border1 {
    border: 1px solid black;
    border-radius: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
    width: 80%;
  }
  .data {
    display: inline-block;
    width: 20%;
  }

  .fleft {
    margin-left: 10%;
  }
</style>
