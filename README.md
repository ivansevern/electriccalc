# electriccalc
package com.example.electiccalc;





import androidx.appcompat.app.AppCompatActivity;

import android.graphics.PorterDuff;
import android.os.Bundle;
import android.text.Editable;
import android.text.TextWatcher;
import android.view.Gravity;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.ImageView;
import android.widget.LinearLayout;
import android.widget.RadioButton;
import android.widget.TextView;
import android.widget.Toast;


public class MainActivity extends AppCompatActivity {
    private EditText cos;
    private EditText P;
    private EditText I;
    private TextView IView;
    private TextView PView;
    private Button button;
    private Button button1;
    private Button button2;
    private Button button3;
    private RadioButton rb12;
    private RadioButton rb24;
    private RadioButton rb36;
    private RadioButton rb220;
    private RadioButton rb380;
    private RadioButton rb6000;
    private RadioButton rb10000;





    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        IView = (TextView) findViewById(R.id.IView);
        PView = (TextView) findViewById(R.id.PView);
        button = (Button) findViewById(R.id.button);
        button1 = (Button) findViewById(R.id.button1);
        button2 = (Button) findViewById(R.id.button2);
        button3 = (Button) findViewById(R.id.button3);
        cos = (EditText) findViewById(R.id.cos);
        P = (EditText) findViewById(R.id.P);
        I = (EditText) findViewById(R.id.I);
        rb12 = (RadioButton) findViewById(R.id.rb12);
        rb24 = (RadioButton) findViewById(R.id.rb24);
        rb36 = (RadioButton) findViewById(R.id.rb36);
        rb220 = (RadioButton) findViewById(R.id.rb220);
        rb380 = (RadioButton) findViewById(R.id.rb380);
        rb6000 = (RadioButton) findViewById(R.id.rb6000);
        rb10000 = (RadioButton) findViewById(R.id.rb10000);





        button3.setOnClickListener(new View.OnClickListener()

        {
            @Override
            public void onClick (View v){
            /*    Toast toast = Toast.makeText(getApplicationContext(),R.string.app_name, Toast.LENGTH_LONG);
                toast.setGravity(Gravity.CENTER, 1, -1);
                LinearLayout toastContainer = (LinearLayout)toast.getView();          // вывод рисунка в сообщение
                ImageView mainImageView = new ImageView(getApplicationContext());
                mainImageView.setImageResource(R.drawable.main);   //вызов рисунка
                toastContainer.addView(mainImageView, 0);
                toast.show();  */

                Toast toast = Toast.makeText(getApplicationContext(),
                        " 1.Введите косинус фи                                    " +
                                " (если не известен введите 1)   " +
                                "                     2. Введите изветную мощность (в кВт) " +
                                "   3. Введите известный ток (в А)" +
                                " 4. Выберите справо напряжение " +
                                " 5. Нажмите ПЕРЕВОД (искомых данных)" +
                                " 6. При новом расчете " +
                                " нажмите сброс ", Toast.LENGTH_LONG);
                toast.setGravity(Gravity.CENTER, 0, 0);   // расположение
                toast.show();
            }
        });


        P.addTextChangedListener(pTextWatcher);                                           //проверка едит на ввод
        I.addTextChangedListener(pTextWatcher);
        cos.addTextChangedListener(pTextWatcher);
    }

    private TextWatcher pTextWatcher = new TextWatcher() {
        @Override
        public void beforeTextChanged(CharSequence s, int start, int count, int after) {
            String PInput = P.getText().toString().trim();                                    //ввод в эдит
            String IInput = I.getText().toString().trim();
            String cosInput = cos.getText().toString().trim();
            button.setEnabled(!PInput.isEmpty() && !cosInput.isEmpty());                      //если едит П и эдит кос пустые отключаем кнопку
            button1.setEnabled(!IInput.isEmpty() && !cosInput.isEmpty());
        }

        @Override
        public void onTextChanged(CharSequence s, int start, int before, int count) {
            String PInput = P.getText().toString().trim();                                    //ввод в эдит
            String IInput = I.getText().toString().trim();
            String cosInput = cos.getText().toString().trim();

            button.setEnabled(!PInput.isEmpty() && !cosInput.isEmpty());                      //если едит П и эдит кос пустые отключаем кнопку
            button1.setEnabled(!IInput.isEmpty() && !cosInput.isEmpty());


        }

        @Override
        public void afterTextChanged(Editable s) {
            final String PInput = P.getText().toString().trim();                                    //ввод в эдит
            String IInput = I.getText().toString().trim();
            String cosInput = cos.getText().toString().trim();
            button.setEnabled(!PInput.isEmpty() && !cosInput.isEmpty());                      //если едит П и эдит кос пустые отключаем кнопку

            button1.setEnabled(!IInput.isEmpty() && !cosInput.isEmpty());






            button.setOnClickListener(new View.OnClickListener()

            {
                @Override
                public void onClick (View v){

                    double a;
                    double b;
                    double c;
                    double i;
                    double k;
                    k = Math.sqrt(3);


                    if (rb12.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 12;
                        i = (b * 1000) / (c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb24.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 24;
                        i = (b * 1000) / (c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb36.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 36;
                        i = (b * 1000) / (c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb220.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 220;
                        i = (b * 1000) / (c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb380.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 380;
                        i = (b * 1000) / (k * c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb6000.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 6000;
                        i = (b * 1000) / (k * c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));
                    }
                    if (rb10000.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = P.getText().toString();
                        a = Double.parseDouble(S1);
                        b = Double.parseDouble(S2);
                        c = 10000;
                        i = (b * 1000) / (k * c) / a;
                        String S = Double.toString(i);
                        IView.setText(String.format("%.2f", i));

                    }



                }

            });
            button1.setOnClickListener(new View.OnClickListener()

            {
                @Override
                public void onClick (View v){
                    double a;  //cos
                    double b;  //P
                    double c;  //U
                    double i;
                    double k;  //cor
                    double p;
                    k = Math.sqrt(3);


                    if (rb12.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 12;
                        p = (c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb24.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 24;
                        p = (c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb36.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 36;
                        p = (c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb220.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 220;
                        p = (c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb380.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 380;
                        p = (k * c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb6000.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 6000;
                        p = (k * c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));
                    }
                    if (rb10000.isChecked()) {
                        String S1 = cos.getText().toString();
                        String S2 = I.getText().toString();
                        a = Double.parseDouble(S1);
                        i = Double.parseDouble(S2);
                        c = 10000;
                        p = (k * c * i * a) / 1000;
                        String S = Double.toString(p);
                        PView.setText(String.format("%.2f", p));

                    }
                }
            });

            button2.setOnClickListener(new View.OnClickListener()

            {
                @Override
                public void onClick (View v){
                    IView.setText("");
                    PView.setText("");
                    P.getText().clear();
                    I.getText().clear();
                    cos.getText().clear();
                }
            });


        }
    };
}



















