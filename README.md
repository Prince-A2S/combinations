cpp
Copy code
void backtrack(string& digits, int index, string& current, vector<string>& result, vector<string>& mapping) {
    if (index == digits.size()) {
        result.push_back(current);
        return;
    }
    for (char ch : mapping[digits[index] - '0']) {
        current.push_back(ch);
        backtrack(digits, index + 1, current, result, mapping);
        current.pop_back();
    }
}

vector<string> letterCombinations(string digits) {
    if (digits.empty()) return {};
    vector<string> mapping = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
    vector<string> result;
    string current;
    backtrack(digits, 0, current, result, mapping);
    return result;
}
