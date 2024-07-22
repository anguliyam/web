<div class="container">
    <div class="text">Coming Soon</div>
  </div>
  <style>
    .container {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(135deg, #000, #fff); /* White and black gradient */
      overflow: hidden;
      position: relative;
    }
  
    .text {
      font-size: 3rem;
      color: white;
      text-transform: uppercase;
      font-weight: bold;
      opacity: 0;
      animation: fadeIn 2s ease-in-out forwards, bounce 2s ease-in-out infinite;
    }
  
    @keyframes fadeIn {
      to {
        opacity: 1;
      }
    }
  
    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
      }
      40% {
        transform: translateY(-30px);
      }
      60% {
        transform: translateY(-15px);
      }
    }
    
    @media (max-width: 768px) {
      .text {
        font-size: 2rem; /* Adjust font size for smaller screens */
      }
    }
  
    @media (max-width: 480px) {
      .text {
        font-size: 1.5rem; /* Further adjust font size for very small screens */
      }
    }
  </style>
  