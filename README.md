# Cpp-Practice-Code
// Program to create a folder and list its contents #include <iostream> #include <filesystem>

namespace fs = std::filesystem;

int main() { std::string folderName = "TestFolder";

// Create a folder
if (!fs::exists(folderName)) {
    if (fs::create_directory(folderName)) {
        std::cout << "Folder created: " << folderName << std::endl;
    } else {
        std::cout << "Failed to create folder." << std::endl;
        return 1;
    }
} else {
    std::cout << "Folder already exists: " << folderName << std::endl;
}

// Create sample files inside the folder (for demonstration)
std::ofstream(folderName + "/file1.txt").put('a');
std::ofstream(folderName + "/file2.txt").put('b');

// List contents of the folder
std::cout << "Contents of " << folderName << ":" << std::endl;
for (const auto& entry : fs::directory_iterator(folderName)) {
    std::cout << " - " << entry.path().filename() << std::endl;
}

return 0;

}


