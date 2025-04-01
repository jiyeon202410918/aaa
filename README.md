// Arduino Piano Project

#define BUZZER_PIN 3  // 피에조 부저 연결 핀

// 버튼 핀 배열 (D2 ~ D9 사용)
int buttonPins[] = {2, 3, 4, 5, 6, 7, 8, 9};

// 각 버튼에 해당하는 음의 주파수 (도~높은 도)
int tones[] = {262, 294, 330, 349, 392, 440, 494, 523};

void setup() {
    pinMode(BUZZER_PIN, OUTPUT);
    for (int i = 0; i < 8; i++) {
        pinMode(buttonPins[i], INPUT_PULLUP); // 풀업 저항 활성화
    }
}

void loop() {
    for (int i = 0; i < 8; i++) {
        if (digitalRead(buttonPins[i]) == LOW) { // 버튼이 눌리면
            tone(BUZZER_PIN, tones[i]);  // 해당 음 재생
            delay(200);  // 소리 지속 시간
            noTone(BUZZER_PIN);  // 소리 끄기
        }
    }
}
