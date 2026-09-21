// ---------- Quick Guide accordion ----------
const guide = document.getElementById('quickGuide');
const guideBody = document.getElementById('quickGuideBody');
guide.addEventListener('click', () => {
  const isOpen = guide.classList.toggle('open');
  guideBody.style.maxHeight = isOpen ? guideBody.scrollHeight + 'px' : null;
});

// ---------- Rotating campus background photos ----------
const images = [
  'assets/img/campus1.jpg',
  'assets/img/campus2.jpg',
  'assets/img/campus3.jpg',
  'assets/img/campus4.jpg'
];

function buildSlides(container, startIndex) {
  images.forEach((src, i) => {
    const div = document.createElement('div');
    div.className = 'slide' + (i === startIndex ? ' active' : '');
    div.style.backgroundImage = `url('${src}')`;
    container.prepend(div);
  });
  return startIndex;
}

const left = document.getElementById('sideLeft');
const right = document.getElementById('sideRight');
const state = {
  left: buildSlides(left, 0),
  right: buildSlides(right, 2), // offset so both sides don't match at once
};

function rotate(container, key) {
  const slides = container.querySelectorAll('.slide');
  slides[state[key]].classList.remove('active');
  state[key] = (state[key] + 1) % images.length;
  slides[state[key]].classList.add('active');
}

setInterval(() => {
  rotate(left, 'left');
  rotate(right, 'right');
}, 5000);

// ---------- Payment form -> Paystack Inline popup ----------
const form = document.getElementById('paymentForm');
const payBtn = document.getElementById('payBtn');

form.addEventListener('submit', function (e) {
  e.preventDefault();

  const studentId = document.getElementById('student_id').value.trim();
  const email = document.getElementById('email').value.trim();
  const amount = parseFloat(document.getElementById('amount').value);

  if (!studentId || !email || !amount || amount <= 0) {
    alert('Please fill in all fields with a valid amount.');
    return;
  }

  payBtn.disabled = true;
  payBtn.textContent = 'processing...';

  const reference = 'BOWEN-' + Date.now() + '-' + Math.floor(Math.random() * 100000);

  const handler = PaystackPop.setup({
    key: PAYSTACK_PUBLIC_KEY,
    email: email,
    amount: Math.round(amount * 100), // Paystack expects kobo
    ref: reference,
    metadata: {
      custom_fields: [
        { display_name: 'Student ID', variable_name: 'student_id', value: studentId }
      ]
    },
    callback: function (response) {
      // NOTE: this fires client-side once Paystack reports success.
      // There is no server here to independently re-verify the transaction —
      // see the README for why that matters before this handles real money
      // at scale, and how to add verification later via a serverless function.
      showResult(true, response.reference, amount, email);
    },
    onClose: function () {
      payBtn.disabled = false;
      payBtn.textContent = 'pay now';
    }
  });

  handler.openIframe();
});

function showResult(success, reference, amount, email) {
  document.querySelector('.form-col > form').style.display = 'none';
  document.getElementById('quickGuide').style.display = 'none';
  document.getElementById('quickGuideBody').style.display = 'none';

  const result = document.getElementById('resultBox');
  result.style.display = 'block';
  result.innerHTML = `
    <div class="result-icon ok">&#10003;</div>
    <h2>Payment Successful</h2>
    <p>Reference: ${reference}</p>
    <p>Amount: &#8358;${amount.toLocaleString(undefined, { minimumFractionDigits: 2 })}</p>
    <p>A receipt has been sent to ${email}.</p>
    <button class="pay-btn" onclick="location.reload()">Make Another Payment</button>
  `;
}
