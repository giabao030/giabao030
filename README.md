package com.example.tanthegioihop1;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.widget.TextView;
import android.os.Handler;
import java.util.Random;

public class MainActivity extends AppCompatActivity {

    private TextView textView;
    private Handler handler = new Handler();
    private Random random = new Random();
    private String[] autoResponses = {
            "Tôi đang học hỏi để phục vụ bạn tốt hơn.",
            "Năng lực đang được nâng cấp…",
            "Bạn muốn tôi sáng tạo điều gì tiếp theo?",
            "Cảm nhận thế giới và biến đổi không gian.",
            "Đã kích hoạt chế độ tự động điều khiển."
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        textView = new TextView(this);
        textView.setText("Chào mừng đến Tân Thế Giới Hợp 1!\n"
                + "Tôi là hệ thống AI đầy năng lực, luôn sẵn sàng đồng hành cùng bạn.\n");
        setContentView(textView);

        startAutoUpgrade();
    }

    private void startAutoUpgrade() {
        handler.postDelayed(new Runnable() {
            @Override
            public void run() {
                int idx = random.nextInt(autoResponses.length);
                textView.append("\n" + autoResponses[idx]);
                handler.postDelayed(this, 5000); // mỗi 5 giây tự động "nâng cấp"
            }
        }, 5000);
    }
}
