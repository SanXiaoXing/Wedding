<template>
    <div>
    <div id="banner">
        <div class="img-list img-wrapper">
            <div class="img-box">
                <img src="../image/image1.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image2.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image3.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image4.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image5.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image6.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image7.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image8.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image9.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image10.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image11.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image12.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image13.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image14.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image15.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image16.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image17.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image18.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image19.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image20.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image21.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image22.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image23.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image24.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image25.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image26.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image27.jpg" alt="">
            </div>
            <div class="img-box">
                <img src="../image/image28.jpg" alt="">
            </div>
            <div class="img-box" id="last-img-box">
                <img src="../image/image29.jpg" alt="">
            </div>
        </div>
    </div>
    <div class="btn-group">
        <button class="last btn">
            <svg t="1686471404424" class="icon left" viewBox="0 0 1024 1024" version="1.1"
                xmlns="http://www.w3.org/2000/svg" p-id="2373" width="128" height="128">
                <path
                    d="M862.485 481.154H234.126l203.3-203.3c12.497-12.497 12.497-32.758 0-45.255s-32.758-12.497-45.255 0L135.397 489.373c-12.497 12.497-12.497 32.758 0 45.254l256.774 256.775c6.249 6.248 14.438 9.372 22.627 9.372s16.379-3.124 22.627-9.372c12.497-12.497 12.497-32.759 0-45.255l-203.3-203.301h628.36c17.036 0 30.846-13.81 30.846-30.846s-13.81-30.846-30.846-30.846z"
                    fill="" p-id="2374"></path>
            </svg>
        </button>
        <button class="next btn">
            <svg t="1686471404424" class="icon right" viewBox="0 0 1024 1024" version="1.1"
                xmlns="http://www.w3.org/2000/svg" p-id="2373" width="128" height="128">
                <path
                    d="M862.485 481.154H234.126l203.3-203.3c12.497-12.497 12.497-32.758 0-45.255s-32.758-12.497-45.255 0L135.397 489.373c-12.497 12.497-12.497 32.758 0 45.254l256.774 256.775c6.249 6.248 14.438 9.372 22.627 9.372s16.379-3.124 22.627-9.372c12.497-12.497 12.497-32.759 0-45.255l-203.3-203.301h628.36c17.036 0 30.846-13.81 30.846-30.846s-13.81-30.846-30.846-30.846z"
                    fill="" p-id="2374"></path>
            </svg>
        </button>
    </div>
</div>
</template>

<script>
export default {
  mounted() {
    // 将上述代码段复制粘贴到这里
        const imgListOne = document.querySelector('.img-list')
        // 获取图片类数组，并将其转化为数组
        let imgBoxList = Array.prototype.slice.call(document.querySelectorAll('.img-list .img-box'))
        const imgBoxCount = imgBoxList.length
        const root = document.documentElement;
        const btnGroup = document.querySelector('.btn-group')
        const lastBtn = document.querySelector('.last')
        const nextBtn = document.querySelector('.next')
        const lastImgBox = document.getElementById('last-img-box')

        // 获取--post-spacing和--post-size的值
        const postSpacing = Number(getComputedStyle(root).getPropertyValue('--post-spacing').replace("vw", ""));
        const postSize = Number(getComputedStyle(root).getPropertyValue('--post-size').replace("vw", ""));

        // 根据图片的数量动态获取img-list的宽度
        let imgListLength = (postSize + postSpacing) * imgBoxCount
        console.log(imgListLength);
        // 根据图片的数量动态获取img-box的宽度
        const imgBoxLength = postSize + postSpacing

        let index = 0
        let timer = null
        let animationTime = 0.5

        // 初始化数组中元素的的顺序，将最后一张图片放在第一位与html部分图片展示位置一致
        imgBoxList.unshift(imgBoxList.pop())
        // 设置imgListOne动画时间
        imgListOne.style.transition = animationTime + 's ease'
        // 设置按钮出现时间
        setTimeout(function () {
            btnGroup.style.opacity = '1'
            btnGroup.style.bottom = '5%'
        }, animationTime * 1000)
        // 点击事件
        function cilckFun(flag) {
            //下一张 next
            if (flag == 'next') {
                index--
                console.log(index);
                // 因为右边没有显示的图片比较多，所以可以直接先整体向左移动
                imgListOne.style.left = imgBoxLength * index + "vw";
                setTimeout(function () {
                    imgListOne.style.transition = 'none'
                    // 当点击下一个累计达到图片数量时，相当于要回到原点，则重置变量和位置
                    if (Math.abs(index) == imgBoxCount) {
                        index = 0
                        imgListOne.style.left = 0
                        imgBoxList.forEach(item => {
                            if (item.id == 'last-img-box') {
                                item.style.transform = `translateX(-160.68vw)`
                            } else {
                                item.style.transform = 'none'
                            }
                        });
                    } else {
                        // 当第一张图片为last-img-box时，说明已经跑完了一轮，则将其放在最后的位置，初始状态其为-160.68vw
                        if (imgBoxList[0].id == 'last-img-box') {
                            lastImgBox.style.transition = 'none'
                            lastImgBox.style.transform = 'translateX(0px)'
                        } else if (index >= 0) {
                            /*  
                                这种情况是为了解决在点击完第last，再点击next时造成的bug问题，其实就是回退，再点击last之前
                                没有加transform属性，点击last以后则添加了transform属性，再次点击next按钮后应该不加transform
                            */
                            imgBoxList[0].style.transform = 'none'
                        } else {
                            // 正常情况下，点击next，则将最左侧的图片移到最后
                            imgBoxList[0].style.transform = 'translateX(160.68vw)'
                        }
                    }
                    // 模拟移动情况，将最左侧的图片（元素）移动到最后
                    imgBoxList.push(imgBoxList.shift())
                }, animationTime * 1000)
            } else {
                // 上一张 last
                index++
                console.log(index);
                // 模拟移动情况，把最右侧的图片（元素）移动到最前
                imgBoxList.unshift(imgBoxList.pop())
                // 因为左侧图片只会有一张，所以需要先移动图片到左侧，再进行imgListOne的移到
                if (imgBoxList[0].id == 'last-img-box' && index != 0) {
                    // 当第一张图片为last-img-box时，说明已经跑完了一轮，此时相对于一开始的位置为-321.36vw
                    imgBoxList[0].style.transform = 'translateX(-321.36vw)'
                } else if (index < 0) {
                    // 这种情况与点击next按钮出现的回退现象一致
                    imgBoxList[0].style.transform = 'none'
                } else {
                    // 正常情况下，点击last，则将最右侧的图片移到最前
                    imgBoxList[0].style.transform = 'translateX(-160.68vw)'
                }
                imgListOne.style.left = imgBoxLength * index + "vw";
                lastImgBox.style.transition = 'none'
                // 当点击下一个累计达到图片数量时，相当于要回到原点，则重置变量和位置
                if (Math.abs(index) == imgBoxCount) {
                    index = 0
                    setTimeout(function () {
                        imgListOne.style.transition = 'none'
                        imgListOne.style.left = 0
                        imgBoxList.forEach(item => {
                            if (item.id == 'last-img-box') {
                                item.style.transform = 'translateX(-160.68vw)'
                            } else {
                                item.style.transform = 'none'
                            }
                        });
                    }, animationTime * 1000)
                }
            }
            imgListOne.style.transition = animationTime + 's ease'
        }

        //节流函数
        function throttle(fn, delay) {
            return function () {
                if (timer) {
                    return
                }
                fn.apply(this, arguments)
                timer = setTimeout(() => {
                    timer = null
                }, delay)
            }
        }

        nextBtn.onclick = throttle(() => cilckFun('next'), animationTime * 1000);

        lastBtn.onclick = throttle(() => cilckFun('last'), animationTime * 1000);
  }
};
</script>

<style>
/* 添加你的样式 */

:root {
  --post-spacing: 1.8vw;
  --post-size: 25vw; 
  --mask-size: 100vw;
}

* {
  padding: 0;
  margin: 0;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}

#banner {
  overflow: hidden;
  position: relative;
  width: 100vw;
  height: calc(var(--post-size) / 0.72);
  -webkit-mask: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNDQwIiBoZWlnaHQ9IjUwMCIgdmlld0JveD0iMCAwIDE0NDAgNTAwIiBpZD0iaiI+CiAgPHBhdGggZmlsbD0icmdiKDIwMCwyMDAsMjAwKSIgZmlsbC1ydWxlPSJldmVub2RkIiBkPSJNMCAwczI3NS4wNCAxMDAgNzIwIDEwMFMxNDQwIDAgMTQ0MCAwdjUwMHMtMjc1LjA0LTEwMC03MjAtMTAwUzAgNTAwIDAgNTAwVjB6Ii8+Cjwvc3ZnPgo=);
          mask: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNDQwIiBoZWlnaHQ9IjUwMCIgdmlld0JveD0iMCAwIDE0NDAgNTAwIiBpZD0iaiI+CiAgPHBhdGggZmlsbD0icmdiKDIwMCwyMDAsMjAwKSIgZmlsbC1ydWxlPSJldmVub2RkIiBkPSJNMCAwczI3NS4wNCAxMDAgNzIwIDEwMFMxNDQwIDAgMTQ0MCAwdjUwMHMtMjc1LjA0LTEwMC03MjAtMTAwUzAgNTAwIDAgNTAwVjB6Ii8+Cjwvc3ZnPgo=);
  -webkit-mask-repeat: no-repeat;
          mask-repeat: no-repeat;
  -webkit-mask-position: center;
          mask-position: center;
  -webkit-mask-size: var(--mask-size);
          mask-size: var(--mask-size);
  position: relative;

}

#banner .img-wrapper {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  position: absolute;
  width: 100%;
  float: left;
  height: calc(var(--post-size) / 0.72);
  -webkit-transform: translate(13.39vw, 0);
          transform: translate(13.39vw, 0);
  -webkit-animation: admission 1.5s;
          animation: admission 1.5s;
}

#banner .img-wrapper .img-box {
  height: 100%;
  display: inline-block;
  margin-right: var(--post-spacing);
  position: relative;
  cursor: pointer;
}

#banner .img-wrapper .img-box .info {
  position: absolute;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  background: rgba(23, 23, 23, 0.5);
  text-align: center;
  color: #fff9f1;
  font-size: 4rem;
}

#banner .img-wrapper .img-box img {
  width: var(--post-size);
  height: 125%;
  -o-object-position: center;
     object-position: center;
  -o-object-fit: cover;
     object-fit: cover;
}

#banner .img-wrapper .img-box:last-child {
  -webkit-transform: translate(-160.68vw, 0);
          transform: translate(-160.68vw, 0);
}

.btn-group {
  height: 15vh;
  position: absolute;
  left: 50%;
  bottom: 0%;
  -webkit-transform: translate(-50%, -50%);
          transform: translate(-50%, -50%);
  -webkit-transition: 1s;
  transition: 1s;
  opacity: 0;
}

.btn-group .btn {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  border: 1px solid #171717;
  background-color: #fff;
  margin: 10px;
  cursor: pointer;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}

.btn-group .btn:hover {
  -webkit-transform: scale(1.2);
          transform: scale(1.2);
  background-color: #000;
}

.btn-group .btn:hover .icon {
  fill: #fff;
}

.btn-group .btn .icon {
  width: 30px;
  height: 30px;
}

.btn-group .btn .right {
  -webkit-transform: rotate(180deg);
          transform: rotate(180deg);
}

.img-list {
  left: 0;
}

@-webkit-keyframes admission {
  0% {
    -webkit-transform: translate(140vw, 0);
            transform: translate(140vw, 0);
  }
  100% {
    -webkit-transform: translate(13.39vw, 0);
            transform: translate(13.39vw, 0);
  }
}

@keyframes admission {
  0% {
    -webkit-transform: translate(140vw, 0);
            transform: translate(140vw, 0);
  }
  100% {
    -webkit-transform: translate(13.39vw, 0);
            transform: translate(13.39vw, 0);
  }
}
/*# sourceMappingURL=style.css.map */

</style>