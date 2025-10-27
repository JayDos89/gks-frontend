<script>
    export let current = '/'; // highlight active route
  </script>
  
  <style>
    nav {
      background-color: #333;
      padding: 0.75rem 1rem;
      display: flex;
      justify-content: center;
      gap: 1.5rem;
    }
  
    a {
      color: white;
      text-decoration: none;
      font-weight: 500;
    }
  
    a:hover {
      text-decoration: underline;
    }
  
    .active {
      border-bottom: 2px solid gold;
    }
  </style>
  
  <nav>
    <a href="/" class:active={current === '/'}> Home</a>
    <a href="/scores" class:active={current === '/scores'}> High Scores</a>
    <a href="/about" class:active={current === '/about'}>ℹ️ About</a>
  </nav>
  