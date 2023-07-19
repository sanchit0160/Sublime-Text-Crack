<div align="center">
  <img height="80" src="https://www.sublimehq.com/images/sublime_text.png">
  <h1>Sublime-Text-Crack</h1>
</div>

<span>Sublime Text [Product Version - 4143] Crack! Last updated: <a href=#20200612><b>19th July, 2023</b></a></span>
---
Note - Do not try this with any other version of Sublime Text.

#### 1. Manipulte HEX Value manually
 	Go to offset 21fe60 and replace 1E to 0B

---
#### 2. Manipulate HEX Value thorugh script
```c++
#include <iostream>
#include <fstream>
#include <vector>
#include <string>
#include <algorithm>
#include <Windows.h>

using namespace std;

vector<size_t> findBytesInFile(const string& filePath, const vector<unsigned char>& bytesToFind) {
    vector<size_t> foundOffsets;

    ifstream file(filePath, ios::in | ios::binary);
    if (!file) {
        cerr << "Error: Unable to open the file: " << filePath << endl;
        return foundOffsets;
    }

    vector<unsigned char> fileContent((istreambuf_iterator<char>(file)), {});

    for (size_t i = 0; i < fileContent.size() - bytesToFind.size() + 1; ++i) {
        if (equal(bytesToFind.begin(), bytesToFind.end(), fileContent.begin() + i)) {
            foundOffsets.push_back(i);
        }
    }

    return foundOffsets;
}

int replaceBytesInFile(const string& filePath, size_t offset, const vector<unsigned char>& newBytes) {
    fstream file(filePath, ios::in | ios::out | ios::binary | ios::ate);
    if (!file) {
        cerr << "Error: Unable to open the file: " << filePath << endl;
        return 0;
    }

    file.seekp(offset, ios::beg);
    file.write(reinterpret_cast<const char*>(newBytes.data()), newBytes.size());

    return 1;
}

int main() {
    TCHAR username[MAX_PATH];
    DWORD usernameLength = MAX_PATH;
    GetUserName(username, &usernameLength);

    string usernameStr(username);

    string copiedFilePath = "C:\\Users\\" + usernameStr + "\\Desktop\\sublime_text.exe";

    if (!CopyFile("C:\\Program Files\\Sublime Text\\sublime_text.exe", copiedFilePath.c_str(), FALSE)) {
        cerr << "Error: Unable to copy the file." << endl;
        return 1;
    }

    string exeFilePath = copiedFilePath;

    vector<unsigned char> searchBytes = { 0x1E };
    vector<unsigned char> replaceBytes = { 0x0B };

    vector<size_t> foundOffsets = findBytesInFile(exeFilePath, searchBytes);

    if (foundOffsets.empty()) {
        cout << "Bytes not found in the file." << endl;
    } else {
        bool offsetFound = find(foundOffsets.begin(), foundOffsets.end(), 0x21fe60) != foundOffsets.end();

        if (offsetFound) {
            cout << "Bytes found at offset: " << hex << 0x21fe60 << endl;

            if (replaceBytesInFile(exeFilePath, 0x21fe60, replaceBytes) != 0) {
                cout << "Bytes replaced successfully." << endl;
                cout << "Now replace the original sublime_text.exe with sublime_text.exe at the Desktop." << endl;
            } else {
                cout << "Error occurred while replacing bytes." << endl;
            }
        } else {
            cout << "Bytes not found at the specified offset." << endl;
        }
    }

    return 0;
}
```
> []()
>
> [](/)

---
