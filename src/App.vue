<template>
  <div id="app">
    <section id="historyquestions" class="questionstyle">
      <div id="question1" v-if="history.q1isDone == false">
        <!-- Göktürk -->
        <h2>Tarihte Türk adıyla kurulan ilk Türk devleti hangisidir?</h2>
        <input v-model="history.q1Value" type="text" />
        <button @click.prevent="hQuestion1">CEVAPLA</button>
        <p v-for="q1Answer in history.q1Answers" :key="q1Answer.id">
          Doğru Cevap: {{ q1Answer }}
        </p>
      </div>
      <div id="question2" v-if="history.q1isDone == true">
        <!-- harzemşahlar -->
        <h2>Siyah bayrak hangi türk devletine aittir ?</h2>
        <input v-model="history.q2Value" type="text" />
        <button @click.prevent="hQuestion2">CEVAPLA</button>
        <p v-for="q2Answer in history.q2Answers" :key="q2Answer.id">
          Doğru Cevap: {{ q2Answer }}
        </p>
      </div>
      <div id="question3" v-if="history.q2isDone == true">
        <!-- selçuklular -->
        <h2>çift başlı kartal hangi Türk Devletinin sembolüdür ?</h2>
        <input v-model="history.q3Value" type="text" />
        <button @click.prevent="hQuestion3">CEVAPLA</button>
        <p v-for="q3Answer in history.q3Answers" :key="q3Answer.id">
          Doğru Cevap : {{ q3Answer }}
        </p>
      </div>
      <div id="question4" v-if="history.q3isDone == true">
        <!-- selçuklular -->
        <h2>Sultan Alparslan hangi devletin yöneticisiydi ?</h2>
        <input v-model="history.q4Value" type="text" />
        <button @click="hQuestion4">CEVAPLA</button>
        <p v-for="q4Answer in history.q4Answers" :key="q4Answer.id">
          Doğru Cevap {{ q4Answer }}
        </p>
      </div>
      <div id="question5" v-if="history.q4isDone == true">
        <!-- göktürk -->
        <h2>Türklerin kullandığı ilk alfabe hangisidir ?</h2>
        <input v-model="history.q5Value" type="text" />
        <button @click.prevent="hQuestion5">CEVAPLA</button>
        <p v-for="q5Answer in history.q5Answers" :key="q5Answer.id">
          Doğru Cevap: {{ q5Answer }}
        </p>
      </div>
    </section>
    <section id="geographyquestions" v-if="history.q5isDone == true">
      <div id="geographyquestion1">
        <h2>
          Maden bakımından zengin olduğu halde endütrisi yeterince gelişmemiş
          olan bölgemiz hangisidir?
        </h2>
        <input v-model="geography.gq1Value" type="text" />
        <button @click.prevent="gQuestion1">CEVAPLA</button>
        <p v-for="gq1Answer in geography.gq1Answers" :key="gq1Answer.id">
          Doğru Cevap: {{ gq1Answer }}
        </p>
      </div>
      <div id="geographyquestion2" v-if="geography.gq1isDone == true">
        <h2>Hiç doğal gölü olmayan bölgemiz hangisidir ?</h2>
        <input v-model="geography.gq2Value" type="text" />
        <button @click.prevent="gQuestion2">CEVAPLA</button>
        <p v-for="gq2Answer in geography.gq2Answers" :key="gq2Answer.id">
          Doğru Cevap: {{ gq2Answer }}
        </p>
      </div>
      <div id="geographyquestion3" v-if="geography.gq2isDone == true">
        <h2>Gübre hangi madenden üretilir ?</h2>
        <input v-model="geography.gq3Value" type="text" />
        <button @click.prevent="gQuestion3">CEVAPLA</button>
        <p v-for="gq3Answer in geography.gq3Answers" :key="gq3Answer.id">
          Doğru Cevap {{ gq3Answer }}
        </p>
      </div>
      <div id="geographyquestion4" v-if="geography.gq3isDone == true">
        <h2>Hangi ilimiz Ermenistan'la komşudur ?</h2>
        <input v-model="geography.gq4Value" type="text" />
        <button @click.prevent="gQuestion4">CEVAPLA</button>
        <p v-for="gq4Answer in geography.gq4Answers" :key="gq4Answer.id">
          Doğru Cevap: {{ gq4Answer }}
        </p>
      </div>
      <div id="geographyquestion5" v-if="geography.gq4isDone == true">
        <h2>En az yağış alan bölgemiz neresidir ?</h2>
        <input v-model="geography.gq5Value" type="text" />
        <button @click.prevent="gQuestion5">CEVAPLA</button>
        <p v-for="gq5Answer in geography.gq5Answers" :key="gq5Answer.id">
          Doğru Cevap: {{ gq5Answer }}
        </p>
      </div>
    </section>
    <section id="mixquestions" v-if="geography.gq5isDone == true">
      <div id="mixquestions1">
        <h2>Kıbrıs Barış harekatı hangi tarihte gerçekleştirmiştir (YIL) ?</h2>
        <input v-model="mixquestions.mq1Value" type="text" />
        <button @click.prevent="mQuestion1">CEVAPLA</button>
        <p v-for="mq1Answer in mixquestions.mq1Answers" :key="mq1Answer.id">
          Doğru Cevap: {{ mq1Answer }}
        </p>
      </div>
      <div id="mixquestions2" v-if="mixquestions.mq1isDone == true">
        <h2>
          Tarihçilerin Kutbu olarak bilinen dünyaca ünlü tarihçimiz kimdir ?
        </h2>
        <input v-model="mixquestions.mq2Value" type="text" />
        <button @click.prevent="mQuestion2">CEVAPLA</button>
        <p v-for="mq2Answer in mixquestions.mq2Answers" :key="mq2Answer.id">
          Doğru Cevap: {{ mq2Answer }}
        </p>
      </div>
      <div id="mixquestions3" v-if="mixquestions.mq2isDone == true">
        <h2>Kuyucaklı Yusuf adlı eser kime aittir?</h2>
        <input v-model="mixquestions.mq3Value" type="text" />
        <button @click.prevent="mQuestion3">CEVAPLA</button>
        <p v-for="mq3Answer in mixquestions.mq3Answers" :key="mq3Answer.id">
          Doğru Cevap: {{ mq3Answer }}
        </p>
      </div>
      <div id="mixquestions4" v-if="mixquestions.mq3isDone == true">
        <h2>1'in türevi kaçtır ? (sayı ile giriniz)</h2>
        <input v-model="mixquestions.mq4Value" type="text" />
        <button @click.prevent="mQuestion4">CEVAPLA</button>
        <p v-for="mq4Answer in mixquestions.mq4Answers" :key="mq4Answer.id">
          Doğru Cevap {{ mq4Answer }}
        </p>
      </div>
      <div id="mixquestions5" v-if="mixquestions.mq4isDone == true">
        <h2>İstiklal Marşı hangi yıl yazılmıştır (Yıl Olarak Giriniz) ?</h2>
        <input v-model="mixquestions.mq5Value" type="text" />
        <button @click.prevent="mQuestion5">CEVAPLA</button>
        <p v-for="mq5Answer in mixquestions.mq5Answers" :key="mq5Answer.id">
          Doğru Cevap: {{ mq5Answer }}
        </p>
      </div>
      <div id="mixquestions6" v-if="mixquestions.mq5isDone == true">
        <h2>Kanuni Sultan Süleyman'ın Eşi kimdir ?</h2>
        <input v-model="mixquestions.mq6Value" type="text" />
        <button @click.prevent="mQuestion6">CEVAPLA</button>
        <p v-for="mq6Answer in mixquestions.mq6Answers" :key="mq6Answer.id">
          Doğru Cevap: {{ mq6Answer }}
        </p>
      </div>
      <div id="mixquestions7" v-if="mixquestions.mq6isDone == true">
        <h2>Kuvvet birimi nedir ?</h2>
        <input v-model="mixquestions.mq7Value" type="text" />
        <button @click.prevent="mQuestion7">CEVAPLA</button>
        <p v-for="mq7Answer in mixquestions.mq7Answers" :key="mq7Answer.id">
          Doğru Cevap: {{ mq7Answer }}
        </p>
      </div>
      <div id="mixquestions8" v-if="mixquestions.mq7isDone == true">
        <h2>1 metre kaç milimetredir ? (Sayı ile Giriniz)</h2>
        <input v-model="mixquestions.mq8Value" type="text" />
        <button @click.prevent="mQuestion8">CEVPALA</button>
        <p v-for="mq8Answer in mixquestions.mq8Answers" :key="mq8Answer.id">
          Doğru Cevap: {{ mq8Answer }}
        </p>
      </div>
      <div id="mixquestions9" v-if="mixquestions.mq8isDone == true">
        <h2>Ankara hangi yıl başkent olmuştur ?</h2>
        <input v-model="mixquestions.mq9Value" type="text" />
        <button @click.prevent="mQuestion9">CEVAPLA</button>
        <p v-for="mq9Answer in mixquestions.mq9Answers" :key="mq9Answer.id">
          Doğru Cevap: {{ mq9Answer }}
        </p>
      </div>
      <div id="mixquestions10" v-if="mixquestions.mq9isDone == true">
        <h2>Çanakkale Zaferi hangi savaşa dahildir ? ( yazı ile )</h2>
        <input v-model="mixquestions.mq10Value" type="text" />
        <button @click.prevent="mQuestion10">CEVAPLA</button>
        <p v-for="mq10Answer in mixquestions.mq10Answers" :key="mq10Answer.id">
          Doğru Cevap: {{ mq10Answer }}
        </p>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      history: {
        q1Value: "",
        q1Answers: [],
        q1isDone: false,
        q2Value: "",
        q2Answers: [],
        q2isDone: false,
        q3Value: "",
        q3Answers: [],
        q3isDone: false,
        q4Value: "",
        q4Answers: [],
        q4isDone: false,
        q5Value: "",
        q5Answers: [],
        q5isDone: false,
      },
      geography: {
        gq1Value: "",
        gq1Answers: [],
        gq1isDone: false,
        gq2Value: "",
        gq2Answers: [],
        gq2isDone: false,
        gq3Value: "",
        gq3Answers: [],
        gq3isDone: false,
        gq4Value: "",
        gq4Answers: [],
        gq4isDone: false,
        gq5Value: "",
        gq5Answers: [],
        gq5isDone: false,
      },
      mixquestions: {
        mq1Value: "",
        mq1Answers: [],
        mq1isDone: false,
        mq2Value: "",
        mq2Answers: [],
        mq2isDone: false,
        mq3Value: "",
        mq3Answers: [],
        mq3isDone: false,
        mq4Value: "",
        mq4Answers: [],
        mq4isDone: false,
        mq5Value: "",
        mq5Answers: [],
        mq5isDone: false,
        mq6Value: "",
        mq6Answers: [],
        mq6isDone: false,
        mq7Value: "",
        mq7Answers: [],
        mq7isDone: false,
        mq8Value: "",
        mq8Answers: [],
        mq8isDone: false,
        mq9Value: "",
        mq9Answers: [],
        mq9isDone: false,
        mq10Value: "",
        mq10Answers: [],
        mq10isDone: false,
      },
    };
  },
  methods: {
    hQuestion1() {
      if (this.history.q1Value.toLowerCase() == "göktürk") {
        this.history.q1Answers.push(this.history.q1Value.toLowerCase());
        this.history.q1isDone = true;
      }
    },
    hQuestion2() {
      if (this.history.q2Value.toLowerCase() == "harzemşahlar") {
        this.history.q2Answers.push(this.history.q2Value.toLowerCase());
        this.history.q2isDone = true;
      }
    },
    hQuestion3() {
      if (this.history.q3Value.toLowerCase() == "selçuklular") {
        this.history.q3Answers.push(this.history.q3Value.toLowerCase());
        this.history.q3isDone = true;
      }
    },
    hQuestion4() {
      if (this.history.q4Value.toLowerCase() == "selçuklular") {
        this.history.q4Answers.push(this.history.q4Value.toLowerCase());
        this.history.q4isDone = true;
      }
    },
    hQuestion5() {
      if (this.history.q5Value.toLowerCase() == "göktürk") {
        this.history.q5Answers.push(this.history.q5Value.toLowerCase());
        this.history.q5isDone = true;
      }
    },
    gQuestion1() {
      if (this.geography.gq1Value.toLowerCase() == "doğu anadolu") {
        this.geography.gq1Answers.push(this.geography.gq1Value.toLowerCase());
        this.geography.gq1isDone = true;
      }
    },
    gQuestion2() {
      if (this.geography.gq2Value.toLowerCase() == "güney doğu anadolu") {
        this.geography.gq2Answers.push(this.geography.gq2Value.toLowerCase());
        this.geography.gq2isDone = true;
      }
    },
    gQuestion3() {
      if (this.geography.gq3Value.toLowerCase() == "fosfat") {
        this.geography.gq3Answers.push(this.geography.gq3Value.toLowerCase());
        this.geography.gq3isDone = true;
      }
    },
    gQuestion4() {
      if (this.geography.gq4Value.toLowerCase() == "ardahan") {
        this.geography.gq4Answers.push(this.geography.gq4Value.toLowerCase());
        this.geography.gq4isDone = true;
      }
    },
    gQuestion5() {
      if (this.geography.gq5Value.toLowerCase() == "iç anadolu") {
        this.geography.gq5Answers.push(this.geography.gq5Value.toLowerCase());
        this.geography.gq5isDone = true;
      }
    },
    mQuestion1() {
      if (this.mixquestions.mq1Value.toLowerCase() == 1974) {
        this.mixquestions.mq1Answers.push(
          this.mixquestions.mq1Value.toLowerCase()
        );
        this.mixquestions.mq1isDone = true;
      }
    },
    mQuestion2() {
      if (this.mixquestions.mq2Value.toLowerCase() == "halil inalcık") {
        this.mixquestions.mq2Answers.push(
          this.mixquestions.mq2Value.toLowerCase()
        );
        this.mixquestions.mq2isDone = true;
      }
    },
    mQuestion3() {
      if (this.mixquestions.mq3Value.toLowerCase() == "sabahattin ali") {
        this.mixquestions.mq3Answers.push(
          this.mixquestions.mq3Value.toLowerCase()
        );
        this.mixquestions.mq3isDone = true;
      }
    },
    mQuestion4() {
      if (this.mixquestions.mq4Value.toLowerCase() == 0) {
        this.mixquestions.mq4Answers.push(
          this.mixquestions.mq4Value.toLowerCase()
        );
        this.mixquestions.mq4isDone = true;
      }
    },
    mQuestion5() {
      if (this.mixquestions.mq5Value.toLowerCase() == 1921) {
        this.mixquestions.mq5Answers.push(
          this.mixquestions.mq5Value.toLowerCase()
        );
        this.mixquestions.mq5isDone = true;
      }
    },
    mQuestion6() {
      if (this.mixquestions.mq6Value.toLowerCase() == "hürrem sultan") {
        this.mixquestions.mq6Answers.push(
          this.mixquestions.mq6Value.toLowerCase()
        );
        this.mixquestions.mq6isDone = true;
      }
    },
    mQuestion7() {
      if (this.mixquestions.mq7Value.toLowerCase() == "newton") {
        this.mixquestions.mq7Answers.push(
          this.mixquestions.mq7Value.toLowerCase()
        );
        this.mixquestions.mq7isDone = true;
      }
    },
    mQuestion8() {
      if (this.mixquestions.mq8Value.toLowerCase() == 1000) {
        this.mixquestions.mq8Answers.push(
          this.mixquestions.mq8Value.toLowerCase()
        );
        this.mixquestions.mq8isDone = true;
      }
    },
    mQuestion9() {
      if (this.mixquestions.mq9Value.toLowerCase() == 1923) {
        this.mixquestions.mq9Answers.push(
          this.mixquestions.mq9Value.toLowerCase()
        );
        this.mixquestions.mq9isDone = true;
      }
    },
    mQuestion10() {
      if (this.mixquestions.mq10Value.toLowerCase() == "birinci dünya savaşı") {
        this.mixquestions.mq10Answers.push(
          this.mixquestions.mq10Value.toLowerCase()
        );
        this.mixquestions.mq10isDone = true;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  margin-top: 150px;
  margin-left: auto;
  margin-right: auto;
}
input {
  padding: 15px;
  border-radius: 10px;
  border: 1px solid black;
}
button {
  padding: 15px;
  margin-left: 5px;
  background-color: black;
  color: white;
  border: 1px solid black;
  border-radius: 10px;
}
</style>