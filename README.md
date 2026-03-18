<!-- 운행일지 폼 예시 -->
<form id="logForm">
  <input type="text" id="driver" placeholder="운전자명">
  <input type="text" id="destination" placeholder="목적지">
  <input type="number" id="distance" placeholder="운행거리(km)">
  <button type="button" onclick="submitLog()">하이웍스에 등록</button>
</form>

<script>
async function submitLog() {
  const logData = {
    title: `[운행일지] ${document.getElementById('driver').value} 차량 운행 기록`,
    content: `
      운전자: ${document.getElementById('driver').value}
      목적지: ${document.getElementById('destination').value}
      운행거리: ${document.getElementById('distance').value} km
    `
  };

  // 1. 내 백엔드 서버로 데이터 전송
  await fetch('/api/send-to-hiworks', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(logData)
  });
  alert('하이웍스에 운행일지가 등록되었습니다!');
}
</script>
