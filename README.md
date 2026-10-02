from math import isqrt


def is_prime(n):
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    for divisor in range(3, isqrt(n) + 1, 2):
        if n % divisor == 0:
            return False
    return True


def primes_in_range(start, end):
    if start > end:
        start, end = end, start
    return [n for n in range(start, end + 1) if is_prime(n)]


def run_tests():
    assert not is_prime(0)
    assert not is_prime(1)
    assert not is_prime(-7)
    assert is_prime(2)
    assert is_prime(3)
    assert not is_prime(4)
    assert is_prime(97)
    assert not is_prime(100)
    assert primes_in_range(1, 20) == [2, 3, 5, 7, 11, 13, 17, 19]
    assert primes_in_range(20, 1) == [2, 3, 5, 7, 11, 13, 17, 19]
    assert primes_in_range(24, 28) == []
    print("All tests passed.")


def main():
    run_tests()
    while True:
        print("\n1) Check a number\n2) List primes in a range\n3) Quit")
        choice = input("Choose: ").strip()
        try:
            if choice == "1":
                n = int(input("Enter a number: "))
                print(f"{n} is {'' if is_prime(n) else 'not '}prime.")
            elif choice == "2":
                a = int(input("Start: "))
                b = int(input("End: "))
                primes = primes_in_range(a, b)
                print(f"{len(primes)} primes found: {primes}")
            elif choice == "3":
                break
            else:
                print("Invalid choice.")
        except ValueError:
            print("Please enter whole numbers only.")


if __name__ == "__main__":
    main()
