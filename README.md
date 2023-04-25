# cube-computation

A Brazil polital dataset is used for this project.

First the data is discretized using the equal width and equal depth methods. 

       inputs:  'data': nx2 numpy array. The raw latitude and longitude columns from the original data,
                                        in the original order.
                'H':    integer.         The number of bins of height/latitude, across the range of all latitudes
                'W':    integer.         The number of bins of width/longitude, across the range of all longitudes
       
       outputs: 'out':  list of ints.    The ith element is the index of the bin in the HxW grid, 
                                        of the ith row in the given 'data', computed H first, e.g.:
                                        | 0 | 3 | 6 |  9 |
                                        | 1 | 4 | 7 | 10 |
                                        | 2 | 5 | 8 | 11 |
                                        for H=3 and W=4

Then the Bottoms-Up Cube computation is done. 

       inputs:  'input':     pandas df      Previously sorted data (see above).
                'curState':  list of str    The current state, as described above
                'dim':       integer.       The starting dimension for this iteration
       globals: 'numDims':   integer.       The total number of dimensions
                'card':      list of ints.  Where card[d] is the cardinality of dimension d
                'minSup':    integer.       The minimum support
                'dataCount': list of lists. dataCount[d] is a list of integers, each of size card[d]
                                            dataCount[d][i] is the size of a partition for variable 'i'
       output:  

All methods are created from scratch, no built-in methods were used.
