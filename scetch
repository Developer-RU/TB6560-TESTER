
# define X_EN     2         // нога енебле -- можно даже не подключать -- зависит от драйвера
# define X_DIR    3         // нога дир
# define X_STP    4         // нога степ


int steps_speed = 3000;     // шагов на разгон и торможение

int min_speed = 1000;       // пауза при минимальной скорости
int max_speed = 100;        // пауза при максимальной скорости
long cycle = 100000;         // колличество шагов на полный цикл


void setup() 
{
    pinMode (X_EN ,OUTPUT); digitalWrite (X_EN,  LOW);
    pinMode (X_DIR ,OUTPUT); digitalWrite (X_DIR,  LOW);
    pinMode (X_STP ,OUTPUT); digitalWrite (X_STP,  LOW);

    // Направление
    digitalWrite (X_DIR,  LOW);
    
    // вправо направление - половина цикла (если от середины начинать - если не нужно - можно удалить)
    for (long i = 0; i < cycle / 2; i++)
    {   
        int s = max_speed;
        
        if(i < steps_speed) 
        {
            s = map(i + max_speed, 0, steps_speed - max_speed, min_speed, max_speed);
        }
        else if(i > ( cycle / 2) - steps_speed)
        {
            s = map(i - max_speed, ( cycle / 2) - steps_speed + max_speed, cycle / 2, max_speed, min_speed);
        }

        digitalWrite(X_STP, HIGH);
        delayMicroseconds(s); 
        digitalWrite(X_STP, LOW);
        delayMicroseconds(s); 
    }
}

void loop() 
{
    // Направление
    digitalWrite (X_DIR,  HIGH);
    
    // вправо направление - полный цикл
    for (long i = 0; i < cycle; i++)
    {   
        int s = max_speed;
        
        if(i < steps_speed) 
        {
            s = map(i + max_speed, 0, steps_speed - max_speed, min_speed, max_speed);
        }
        else if(i > ( cycle ) - steps_speed)
        {
            s = map(i - max_speed, ( cycle ) - steps_speed + max_speed, cycle, max_speed, min_speed);
        }
        
        digitalWrite(X_STP, HIGH);
        delayMicroseconds(s); 
        digitalWrite(X_STP, LOW);
        delayMicroseconds(s); 
    }

    delay(100);

    // Направление
    digitalWrite (X_DIR,  LOW);

    // влево направление - полный цикл
    for (long i = 0; i < cycle; i++)
    {   
        int s = max_speed;
        
        if(i < steps_speed) 
        {
            s = map(i + max_speed, 0, steps_speed - max_speed, min_speed, max_speed);
        }
        else if(i > ( cycle ) - steps_speed)
        {
            s = map(i - max_speed, ( cycle ) - steps_speed + max_speed, cycle, max_speed, min_speed);
        }
        
        digitalWrite(X_STP, HIGH);
        delayMicroseconds(s); 
        digitalWrite(X_STP, LOW);
        delayMicroseconds(s); 
    }
    
    delay(100);
}
