for ( j in 1:Nsubj ) {
  zbeta0[j] ~ dnorm( zbeta0mu , 1/(zbeta0sigma)^2 )  
  zbeta1[j] ~ dnorm( zbeta1mu , 1/(zbeta1sigma)^2 )
  zbeta2[j] ~ dnorm( zbeta2mu , 1/(zbeta2sigma)^2 )
  zbeta3[j] ~ dnorm( zbeta3mu , 1/(zbeta3sigma)^2 )
  }
