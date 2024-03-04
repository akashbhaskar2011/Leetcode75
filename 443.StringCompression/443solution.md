
class Solution {
public:
    int compress(std::vector<char>& c) {
        int j = 0, i = -1, count = 1, ans = 0;
        while (j < c.size()) {
            if (j != c.size() - 1 && c[j] == c[j + 1]) {
                count++;
                j++;
            } else if (count > 1) {
                c[++i] = c[j++];
                ans++;
                
                std::string countStr = std::to_string(count);
                for (char digit : countStr) {
                    c[++i] = digit;
                    ans++;
                }

                count = 1;
            } else {
                c[++i] = c[j++];
                ans++;
            }
        }
        return ans;
    }
};



class Solution {
public:
    int compress(std::vector<char>& c) {
        int j = 0, i = -1, count = 1, ans = 0;
        while (j < c.size()) {
            if (j != c.size() - 1 && c[j] == c[j + 1]) {
                count++;
                j++;
            } else if (count > 1) {
                c[++i] = c[j++];
                ans++;
                if (count >= 10) {
                    c[++i] = (count / 10) + '0';
                    ans++;
                }
                c[++i] = (count % 10) + '0';
                ans++;
                count = 1;
            } else {
                c[++i] = c[j++];
                ans++;
            }
        }
        return ans;
    }
};
