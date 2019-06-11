<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>

    <div class="collapse navbar-collapse">
      <ul class="navbar-nav mr-auto">
        <router-link to="/portfolio" class="nav-item active" tag="li"><a class="nav-link">Portfolio</a></router-link>
        <router-link to="/stocks" class="nav-item active" tag="li"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <ul class="navbar-nav justify-content-end">
          <li class="nav-item p-2"><a class="nav-link"href="#">End Day</a></li>
          <li class="nav-item dropdown nav-link">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"> Save & Load </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Save data</a>
            <a class="dropdown-item" href="#">Load Data</a>
          </div>
        </li>
      </ul>

    </div>
  </nav>
</template>
