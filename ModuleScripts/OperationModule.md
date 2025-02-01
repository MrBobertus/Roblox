```
local OperationModule = {}

-- Basic Operations
-- Addition of two numbers
function MathModule.add(a, b)
	return a + b
end

-- Subtraction of two numbers
function MathModule.subtract(a, b)
	return a - b
end

-- Multiplication of two numbers
function MathModule.multiply(a, b)
	return a * b
end

-- Division of two numbers; raises an error if divisor is zero
function MathModule.divide(a, b)
	if b == 0 then
		return 0
	end
	return a / b
end

-- Get a true or false if the first number is smaller then the second
function MathModule.smaller(a, b)
	return a < b
end

-- Get a true or false if the first number is the same as the second
function MathModule.same(a, b)
	return a == b
end

-- Get a true or false if the first number is bigger then the second
function MathModule.bigger(a, b)
	return a > b
end

-- Advanced Operations
-- Raises base to the power of exponent
function MathModule.power(base, exponent)
	return base ^ exponent
end

-- Computes the square root; raises an error for negative numbers
function MathModule.sqrt(value)
	if value < 0 then
		error("Cannot take square root of a negative number")
	end
	return math.sqrt(value)
end

-- Computes the remainder of division
function MathModule.modulus(a, b)
	return a % b
end

-- Returns the absolute value
function MathModule.absolute(value)
	return math.abs(value)
end

-- Rounds a number to the nearest integer
function MathModule.round(value)
	return math.floor(value + 0.5)
end

-- Rounds a number down to the nearest integer
function MathModule.floor(value)
	return math.floor(value)
end

-- Rounds a number up to the nearest integer
function MathModule.ceil(value)
	return math.ceil(value)
end

-- Trigonometric Functions (angles are in degrees)
-- Computes sine of an angle
function MathModule.sin(angle)
	return math.sin(math.rad(angle))
end

-- Computes cosine of an angle
function MathModule.cos(angle)
	return math.cos(math.rad(angle))
end

-- Computes tangent of an angle
function MathModule.tan(angle)
	return math.tan(math.rad(angle))
end

-- Computes inverse sine and returns result in degrees
function MathModule.asin(value)
	return math.deg(math.asin(value))
end

-- Computes inverse cosine and returns result in degrees
function MathModule.acos(value)
	return math.deg(math.acos(value))
end

-- Computes inverse tangent and returns result in degrees
function MathModule.atan(value)
	return math.deg(math.atan(value))
end

-- Logarithmic Functions
-- Computes logarithm of a value with optional base
function MathModule.log(value, base)
	if base then
		return math.log(value) / math.log(base)
	end
	return math.log(value)
end

-- Computes natural logarithm (base e)
function MathModule.ln(value)
	return math.log(value)
end

-- Computes base-10 logarithm
function MathModule.log10(value)
	return math.log10(value)
end

-- Randomization
-- Generates a random number between min and max, or a random float if no arguments
function MathModule.random(min, max)
	if min and max then
		return math.random(min, max)
	end
	return math.random()
end

-- Seeds the random number generator
function MathModule.randomSeed(seed)
	math.randomseed(seed)
end

-- Time-Based Calculations
-- Calculates time required to travel a distance at a given speed
function MathModule.timeToTravel(distance, speed)
	if speed == 0 then
		error("Speed cannot be zero")
	end
	return distance / speed
end

-- Converts seconds to minutes and seconds
function MathModule.secondsToMinutes(seconds)
	local minutes = math.floor(seconds / 60)
	local remainingSeconds = seconds % 60
	return minutes, remainingSeconds
end

-- Converts minutes to hours and minutes
function MathModule.minutesToHours(minutes)
	local hours = math.floor(minutes / 60)
	local remainingMinutes = minutes % 60
	return hours, remainingMinutes
end

-- Timer function to count down from a given number of seconds
function MathModule.startTimer(amount, seconds, callback)
	spawn(function()
		for i = amount, 1, -1 do
			if seconds then
				wait(seconds)
				if callback then
					callback(i)
				end
			end
		end
	end)
end

-- Complex Operations
-- Computes factorial of n (n!)
function MathModule.factorial(n)
	if n < 0 then
		error("Factorial is not defined for negative numbers")
	elseif n == 0 then
		return 1
	else
		local result = 1
		for i = 2, n do
			result = result * i
		end
		return result
	end
end

-- Computes the nth Fibonacci number
function MathModule.fibonacci(n)
	if n < 0 then
		error("Fibonacci is not defined for negative numbers")
	elseif n == 0 then
		return 0
	elseif n == 1 then
		return 1
	else
		local a, b = 0, 1
		for i = 2, n do
			a, b = b, a + b
		end
		return b
	end
end

-- Game-Relevant Calculations
-- Calculates the distance between two 3D points
function MathModule.distance3D(x1, y1, z1, x2, y2, z2)
	return math.sqrt((x2 - x1)^2 + (y2 - y1)^2 + (z2 - z1)^2)
end

-- Calculates the distance between two 2D points
function MathModule.distance2D(x1, y1, x2, y2)
	return math.sqrt((x2 - x1)^2 + (y2 - y1)^2)
end

-- Calculates lerp (linear interpolation) between two values
function MathModule.lerp(a, b, t)
	return a + (b - a) * t
end

-- Calculates the angle between two points in 2D space
function MathModule.angleBetweenPoints(x1, y1, x2, y2)
	return math.deg(math.atan2(y2 - y1, x2 - x1))
end

-- Calculates velocity given distance and t = time
function MathModule.velocity(distance, t)
	if t == 0 then
		error("Time cannot be zero")
	end
	return distance / t
end

-- Calculates acceleration given initial velocity, final velocity, and t = time
function MathModule.acceleration(v1, v2, t)
	if t == 0 then
		error("Time cannot be zero")
	end
	return (v2 - v1) / t
end

-- DONT ASK it gets kinda boring writing all these...
function MathModule.cheezburger()
	return "cheezburger"
end

return OperationModule
```
