# ELCSK-2011-LongDegugging
genMCMC = function( data , xName="x" , x2Name = "X2", x3Name = "X3", x4Name = "X4", x5Name = "X5", x6Name = "X6", x7Name = "X7", x8Name = "X8", x9Name = "X9", x10Name = "X10", x11Name = "X11", x12Name = "X12", yName="y" , sName="s" ,
                    numSavedSteps=10000 , thinSteps = 1 , saveName=NULL ,
                    runjagsMethod=runjagsMethodDefault , 
                    nChains=nChainsDefault) { 
  
  #-----------------------------------------------------------------------------
  # THE DATA.
  y = data[,yName]
  x = data[,xName]
  x2 = data[,x2Name]
  x3 = data[,x3Name]
  x4 = data[,x4Name]
  x5 = data[,x5Name]
  x6 = data[,x6Name]
  x7 = data[,x7Name]
  x8 = data[,x8Name]
  x9 = data[,x9Name]
  x10 = data[,x10Name]
  x11 = data[,x11Name]
  x12 = data[,x12Name]
  # Convert sName to consecutive integers:
  s = as.numeric(factor(data[,sName]))
  # Do some checking that data make sense:
  if ( any( !is.finite(y) ) ) { stop("All y values must be finite.") }
  if ( any( !is.finite(x) ) ) { stop("All x values must be finite.") }
  #Ntotal = length(y)
  # Specify the data in a list, for later shipment to JAGS:
  dataList = list(
    x = x ,
    x2 = x2,
    x3 = x3,
    x4 = x4,
    x5 = x5,
    x6 = x6,
    x7 = x7,
    x8 = x8,
    x9 = x9,
    x10 = x10,
    x11 = x11,
    x12 = x12,
    y = y ,
    s = s ,
    Nsubj = max(s)  # should equal length(unique(s))
