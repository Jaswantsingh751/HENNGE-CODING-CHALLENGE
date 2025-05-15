# HENNGE-CODING-CHALLENGE
For HENNGE-coding-challenge
def main():
    import sys

    def process_lines(lines, idx, count, results):
        if count == 0:
            return results
        x_line = lines[idx].strip()
        data_line = lines[idx + 1].strip()
        try:
            x = int(x_line)
            y_strs = data_line.split()
            if len(y_strs) != x:
                return process_lines(lines, idx + 2, count - 1, results + [-1])
            nums = list(map(int, y_strs))
            total = sum(map(lambda n: n**4 if n < 0 else 0, nums))
            return process_lines(lines, idx + 2, count - 1, results + [total])
        except:
            return process_lines(lines, idx + 2, count - 1, results + [-1])

    input_data = sys.stdin.read().splitlines()
    if not input_data:
        return

    try:
        n = int(input_data[0].strip())
        outputs = process_lines(input_data, 1, n, [])
        print('\n'.join(map(str, outputs)))
    except:
        pass


if __name__ == "__main__":
    main()
