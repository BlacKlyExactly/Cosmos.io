<template>
    <div class="bug">
      <div class="title">Bug ? Tell us. FAST!!</div>
      <form method="POST" action="https://formspree.io/supreme24d@gmail.com">
        <span>Email</span><input type="email" name="email" placeholder="Your email">
        <span>Bug</span><textarea name="Bug" placeholder="bug"></textarea>
        <button type="submit" class="button">Send Bug</button>
      </form>
    </div>
</template>

<script>
    export default {
        name: "FindBug"
    }
</script>

<style scoped lang="scss">
.bug{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
form{
  display: flex;
  flex-direction: column;
  width: 80vw;
  button{
    margin-bottom: 2vw;
  }
  span{
    margin-bottom: 2vw;
    font-size: 2vw;
  }
  input[type="email"]{
    border-bottom: .2vw solid #FE0090;
    border-top: none;
    border-left: none;
    border-right: none;
    width: 80vw;
    font-size: 2vw;
    color: #FE0090;
    margin-bottom: 5vw;
  }
 textarea{
    border: .2vw solid #FE0090;
    width: 80vw;
    font-size: 2vw;
    color: #FE0090;
    margin-bottom: 5vw;
   resize: none;
   height: 30vw;
  }
}
}
.title{
  font-size: 4.5vmin;
  color: #FE0090;
  margin-bottom: 10vw;
  width: 40vw;
}
</style>
