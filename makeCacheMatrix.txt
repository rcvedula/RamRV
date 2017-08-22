# Inversion of a Matrix consumes system resources and thus affects the costs
# Hence it would be prudent to cache the inverse of a matrix rather than compute it repeatedly
# This program accomplishes this task
# The function makeCacheMatrix does the following:
# Sets the value
# Gets the value
# Then sets the value of inverse
# Finally gets the value of inverse of the matrix
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
# cacheSolution function first checks whether the inverse of the matrix is already computed and available in Cache
# If the inverse is available and there are no changes in the matrix, then cacheSolution will retrieve the inverse from cache
# Else cacheSolution function computes the inverse of matrix using the above function makeCacheMatrix and sends the output
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
