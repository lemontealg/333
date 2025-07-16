addEventListener('fetch', event => {
  event.respondWith(fetchAndReplace(event.request))
})

async function fetchAndReplace(request) {
  // 将下方替换成你的网址2
  const target_url = "[https://真实网址2.com](https://chat.deepseek.com/a/chat/s/958b0a60-9665-41fe-bb5b-60cb8b9d3aa9)" 
  const response = await fetch(target_url)
  
  // 关键设置：强制地址栏显示网址1
  return new Response(response.body, {
    headers: {
      'Content-Type': response.headers.get('Content-Type'),
      'Content-Security-Policy': "frame-ancestors 'self'" // 防止被嵌套
    }
  })
}
