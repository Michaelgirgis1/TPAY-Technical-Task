<template>
  <div class="header-section ">
    <div class="container">
    <div class="row">
      <div class="col-lg-7 col-md-10">
        <div class="header-section__logo">
          <img src="../assets/images/logo.jpg" alt="logo image" />
        </div>
        <div class="header-section__search">
          <span class="icon-search"></span>
          <div>
            <b-dropdown
              size="lg"
              variant="link"
              toggle-class="text-decoration-none"
              no-caret
            >
              <template #button-content>
                <b-icon icon="three-dots-vertical" font-scale="4"></b-icon>
              </template>
              <b-dropdown-item href="#">log in</b-dropdown-item>
              <b-dropdown-item href="#">sign in</b-dropdown-item>
            </b-dropdown>
          </div>
        </div>
      </div>
    </div>

    </div>
  </div>
</template>

<style lang="scss">
.header-section {
  background-color: #fff;
  .row {
    > div {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 0 auto;
      padding: 0;
    }
  }
  .header-section__logo {
    img {
      max-height: 85px;
    }
  }
  .header-section__search {
    display: flex;
    justify-content: center;
    align-items: center;
    .icon-search {
      margin-right: 20px;
      &::before {
    color: #572589;

      }
    }
  }
  button#__BVID__8__BV_toggle_ {
    padding: 0 !important;
    font-size: 6px;
    width: 11px;
    display: flex;
    justify-content: center;
    &:focus {
      box-shadow: unset;
    }
  }
  svg.bi-three-dots-vertical.b-icon.bi {
    color: #572589;
    outline: 0;
  }
  .btn-link {
    &:hover {
      color: unset !important;
    }
  }
  .dropdown-menu {
    left: unset !important;
    right: 0 !important;
  } 
}
@media (max-width: 768px) {
  .header-section {
      .header-section__search{
          margin-right: 20px;
      }
     .dropdown-menu {
       transform: translate3d(0px, 26px, 0px) !important;
     }
  }
}
</style>