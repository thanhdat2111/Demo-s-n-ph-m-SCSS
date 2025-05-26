// Biến toàn cục
$primary-color: #3498db;
$font-stack: Helvetica, sans-serif;
$btn-bg: #2ecc71;
$btn-hover: darken($btn-bg, 10%);
$header-bg: #f4f4f4;
$overlay-bg: rgba(0, 0, 0, 0.5);

// Mixin cho responsive
@mixin respond-to($breakpoint) {
  @if $breakpoint == "small" {
    @media (max-width: 600px) { @content; }
  } @else if $breakpoint == "medium" {
    @media (max-width: 900px) { @content; }
  }
}

// Style cơ bản
body {
  font-family: $font-stack;
  color: $primary-color;
  margin: 0;
  padding: 0;
  background-color: #f9f9f9;

  header {
    background-color: $header-bg;
    padding: 30px;
    text-align: center;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);

    h1 {
      font-size: 3em;
      color: darken($primary-color, 10%);
      margin: 0;
    }

    p {
      font-size: 1.3em;
      margin: 10px 0;
      color: #666;
    }
  }

  .content, .features, .product-section {
    padding: 30px;
    margin: 30px 0;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);

    h2 {
      font-size: 2.2em;
      color: $primary-color;
      margin-bottom: 20px;
    }

    p {
      line-height: 1.7;
      font-size: 1.1em;
      color: #333;
    }

    img {
      max-width: 100%;
      height: auto;
      border: 2px solid $primary-color;
      border-radius: 5px;
      margin: 15px 0;
    }

    ul {
      list-style-type: square;
      padding-left: 25px;
      color: #333;

      li {
        margin: 10px 0;
      }
    }
  }

  .travel-highlights {
    margin-top: 20px;

    h3 {
      font-size: 1.5em;
      color: $primary-color;
      margin-bottom: 10px;
    }

    .highlight-images {
      display: flex;
      gap: 20px;
      justify-content: center;
      flex-wrap: wrap;

      .highlight-item {
        position: relative;
        width: 200px;
        height: 150px;
        overflow: hidden;
        border: 2px solid $primary-color;
        border-radius: 5px;
        cursor: pointer;

        .default-img, .hover-img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          position: absolute;
          top: 0;
          left: 0;
          transition: opacity 0.3s ease;
        }

        .hover-img {
          opacity: 0;
        }

        &:hover .default-img {
          opacity: 0;
        }

        &:hover .hover-img {
          opacity: 1;
        }

        p {
          position: absolute;
          bottom: 5px;
          left: 50%;
          transform: translateX(-50%);
          color: white;
          font-size: 16px;
          background-color: rgba(0, 0, 0, 0.6);
          padding: 5px 10px;
          border-radius: 3px;
        }
      }
    }
  }
}

// Container responsive
.container {
  width: 80%;
  margin: 0 auto;

  @include respond-to("small") {
    width: 100%;
    padding: 10px;
  }
}

// Product list
.product-section {
  .product-list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;

    .product-item {
      width: 200px;
      text-align: center;
      padding: 15px;
      background-color: #f9f9f9;
      border-radius: 5px;
      position: relative;
      transition: transform 0.3s ease;

      &:hover {
        transform: translateY(-5px);
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      }

      .product-image {
        position: relative;

        img {
          width: 100%;
          height: 200px;
          object-fit: cover;
          border-radius: 5px;
        }

        .overlay {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          background-color: $overlay-bg;
          opacity: 0;
          transition: opacity 0.3s ease;
          border-radius: 5px;

          .new-label {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: #e74c3c;
            color: white;
            padding: 5px 10px;
            font-size: 12px;
            border-radius: 3px;
          }
        }

        &:hover .overlay {
          opacity: 1;
        }
      }

      h3 {
        font-size: 16px;
        margin: 10px 0 5px;
        color: #333;
      }

      .price {
        font-size: 14px;
        color: #333;

        .old-price {
          text-decoration: line-through;
          color: #999;
          margin-left: 5px;
        }
      }

      .buttons {
        margin-top: 10px;
        display: flex;
        justify-content: center;
        gap: 10px;

        .view-btn, .cart-btn {
          padding: 5px 10px;
          font-size: 12px;
          text-decoration: none;
          border-radius: 3px;
          transition: background-color 0.3s ease;
        }

        .view-btn {
          background-color: $primary-color;
          color: white;
        }

        .cart-btn {
          background-color: $btn-bg;
          color: white;

          &:hover {
            background-color: $btn-hover;
          }
        }
      }
    }
  }
}

// Style cho button
.button {
  background-color: $btn-bg;
  color: white;
  padding: 12px 25px;
  border: none;
  cursor: pointer;
  margin: 5px;
  border-radius: 5px;
  transition: background-color 0.3s ease;

  &:hover {
    background-color: $btn-hover;
  }

  &.disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }
}

// Style cho footer
footer {
  background-color: $header-bg;
  padding: 20px;
  text-align: center;
  margin-top: 30px;
  border-top: 1px solid #ddd;

  p {
    margin: 0;
    font-size: 1em;
    color: #666;
  }

  .social-links {
    margin: 10px 0;

    .social-icon {
      margin: 0 10px;
      color: $primary-color;
      text-decoration: none;
      font-size: 1.1em;
      display: flex;
      align-items: center;
      gap: 5px;

      i {
        font-size: 1.2em;
      }

      &:hover {
        color: darken($primary-color, 10%);
      }
    }
  }
}
