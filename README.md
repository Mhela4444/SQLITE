# SQLITE

La aplicación contiene un formulario de inicio de sesión simple, un formulario de registro y una lista de usuarios registrados. 

Código xml del diseño.
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="10dp"
    tools:context=".MainActivity">

    <EditText

        android:id="@+id/username"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="50dp"
        android:hint="User Name" />

    <EditText
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/username"
        android:layout_marginTop="29dp"
        android:hint="Password" />

    <EditText
        android:id="@+id/repassword"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/password"
        android:layout_marginTop="38dp"
        android:hint="Retype Password"
        tools:ignore="HardcodedText" />

    <Button
        android:id="@+id/btnsignup"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/repassword"
        android:layout_marginTop="81dp"
        android:text="Register" />

    <Button
        android:id="@+id/btnsignin"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/btnsignup"
        android:layout_marginTop="27dp"
        android:text="Existing user! Go to Sign in page"
        tools:ignore="HardcodedText" />


</RelativeLayout>

Se crea una nueva actividad llamada "LoginActivity". Se accede al archivo XML de diseño de la actividad llamado "actividad_login.xml".
     Se cambia el diseño de restricción a diseño relativo y se agregan los componentes necesarios, nombres e IDs.

     public class LoginActivity extends AppCompatActivity {

    EditText username, password;
    Button btnlogin;
    DBHelper DB;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_login);

        username = (EditText) findViewById(R.id.username1);
        password = (EditText) findViewById(R.id.password1);
        btnlogin = (Button) findViewById(R.id.btnsignin1);
        DB = new DBHelper(this);

        btnlogin.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View view) {

                String user = username.getText().toString();
                String pass = password.getText().toString();

                if(user.equals("")||pass.equals(""))
                    Toast.makeText(LoginActivity.this, "Please enter all the fields", Toast.LENGTH_SHORT).show();
                else{
                    Boolean checkuserpass = DB.checkusernamepassword(user, pass);
                    if(checkuserpass==true){
                        Toast.makeText(LoginActivity.this, "Sign in successfull", Toast.LENGTH_SHORT).show();
                        Intent intent  = new Intent(getApplicationContext(), HomeActivity.class);
                        startActivity(intent);
                    }else{
                        Toast.makeText(LoginActivity.this, "Invalid Credentials", Toast.LENGTH_SHORT).show();
                    }
                }
            }
        });
    }
}
	Se crea otra actividad llamada "HomeActivity".
Esta actividad permitirá al usuario moverse a diferentes páginas una vez que el registro sea exitoso.

![image](https://github.com/Mhela4444/SQLITE/assets/133244582/81d00bb0-c966-4281-b60f-53844ce6effb)



Diseño de inicio de sesión:

![image](https://github.com/Mhela4444/SQLITE/assets/133244582/2545c27e-5b81-48c3-bcc9-d653394dc479)


datos almacenados:

![image](https://github.com/Mhela4444/SQLITE/assets/133244582/da8b43c4-26e5-4934-a309-51edccd1d99b)





