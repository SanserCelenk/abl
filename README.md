# abl
Atmospheric Boundary Layer

// To define atmospheric boundary layer 
// U(45)=3 m/s
// Uabl= 0.321 m/s
// k=0.34347

// U= (Uabl/k).ln[(z+z0)/0]
// k= [(Uabl)^2]/(c)^(1/2)
// e= [(Uabl)^3]/[k(z+z0)]

#include "udf.h"


DEFINE_PROFILE(inlet_x_velocity, thread, position)

{

real x[ND_ND];

real z; 

face_t f;

begin_f_loop(f, thread)

{

F_CENTROID(x,f,thread);

z = x[2];

F_PROFILE(f, thread, position) = 0.7829 *log(z+1);

}

end_f_loop(f, thread)

}

DEFINE_PROFILE(epsilon, thread, position)

{

real x[ND_ND];

real z;

face_t f;

begin_f_loop(f, thread)

{


F_CENTROID(x,f,thread);

z = x[2];

F_PROFILE(f, thread, position) = 0.0806/(z+1);

}

end_f_loop(f, thread)

}

