makeCacheMatrix <- function(x=numeric()) {
cache <- NULL
setMatrix <- function(newNum) {
x <<- newNum
cache <<- NULL
}
getMatrix <- function() {
    x
}
cacheInverse <- function(solution) {
    cache <<- solution
getInverse <- function() {
    cache
}
list(setMatrix=setMatrix, getMatrix=getMatrix, cacheInverse=cacheInverse, getInverse=getInverse)
}
cacheSolution <- function(p, ...) {
inv <- p$getInverse()
if(!is.null(inv)) {
    message("getting cached data")
    return(inv)
}
data <- p$getMatrix()
inv <- solution(data)
p$catchInverse(inv)
inv
}