<template>
  <main>
    <!-- Hero Section -->
    <header class="hero">
      <div class="hero-overlay text-center">
        <div class="container">
          <h1 class="display-4 fw-bold">당신만을 위한 식단 코치</h1>
          <p class="lead mt-3 mb-4">
            재미있는 설문을 통해 나에게 꼭 맞는 식습관을 찾아보세요!
          </p>
          <router-link
            to="/login"
            class="btn btn-lg btn-success"
            v-if="username == ''"
            >로그인 하기{{ username }}</router-link
          >
          <router-link
            to="/survey"
            class="btn btn-lg btn-success"
            v-if="username != '' && !isSurveyed"
            >지금 설문하기</router-link
          >
        </div>
      </div>
    </header>

    <!-- Features Section -->
    <section class="py-5 bg-light">
      <div class="container">
        <h2 class="section-title text-center mb-5">냠냠코치 기능</h2>
        <div class="row text-center">
          <div class="col-md-4">
            <div class="mb-3 fs-1">🥗</div>
            <h5>개인 맞춤형 식단</h5>
            <p>설문을 기반으로 나의 건강 상태에 맞는 식단을 추천해줍니다.</p>
          </div>
          <div class="col-md-4">
            <div class="mb-3 fs-1">📊</div>
            <h5>식습관 분석</h5>
            <p>흥미롭게 식습관을 진단하고 결과를 시각화합니다.</p>
          </div>
          <div class="col-md-4">
            <div class="mb-3 fs-1">📅</div>
            <h5>일간/주간 관리</h5>
            <p>나의 식단을 캘린더로 관리하고, 쉽게 실천할 수 있어요.</p>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  data() {
    return {
      username: this.$store.state.account.username,
      isSurveyed: this.$store.state.account.isSurveyed,
    };
  },
  created() {
    this.username = this.$store.state.account.username;
    if (
      this.$store.state.account.isSurveyed == undefined ||
      this.$store.state.account.isSurveyed == false
    ) {
      this.isSurveyed = false;
    } else {
      this.isSurveyed = this.$store.state.account.isSurveyed;
    }

    //console.log(this.$store.state.account,this.username,this.isSurveyed)
  },
  methods: {},
};
</script>

<!-- scoped는 이 페이지에서만 css를 설정할때 씀 -->
<style scoped>
.hero {
  background: url('https://images.unsplash.com/photo-1551218808-94e220e084d2')
    no-repeat center center;
  background-size: cover;
  color: white;
  height: 100vh;
  display: flex;
  align-items: center;
}

.hero-overlay {
  background-color: rgba(0, 0, 0, 0.5);
  padding: 80px 20px;
  width: 100%;
}

.section-title {
  font-size: 2rem;
  font-weight: 600;
}
</style>
