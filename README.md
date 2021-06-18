## ISO scenario primary electron emission procedure

---

# `g4_gen1e_100evts.txt`

```
// generates 100 2.457 MeV single electron events

for (var i = 0; i < 100; i++){

       var cos_th = 2.0*(math.random()-0.5);     // range [-1,1]
       var sin_th = math.sin(math.acos(cos_th)); // range [-1,1]
       
       var ph = 6.28318530718 * math.random(); // ramge [0,2pi]
       
       var vx = sin_th * math.cos(ph); // i
       var vy = sin_th * math.sin(ph); // k
       var vz = cos_th;                // j
       
       gen.AddParticle(3, 2457.83,  0, 0, 0, vx,vy,vz);
}
```

---

# `g4_genb2b_100evts.txt`

// generates 100 2.457 MeV back-to-back events

for (var i = 0; i < 100; i++){

       // definition of electron 1's direction

       var cos_th1 = 2.0*(math.random()-0.5);      // range [-1,1]
       var sin_th1 = math.sin(math.acos(cos_th1)); // range [-1,1]
       
       var ph1 = 6.28318530718 * math.random(); // range [0,2pi]
       
       var vx1 = sin_th1 * math.cos(ph1); // i
       var vy1 = sin_th1 * math.sin(ph1); // k (I checked src code)
       var vz1 = cos_th1;                 // j
       
       gen.AddParticle(3, 1228.915,  0, 0, 0, vx1,vy1,vz1);              
       gen.AddParticle(3, 1228.915,  0, 0, 0, -vx1,-vy1,-vz1);
}