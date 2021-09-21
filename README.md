#include "MemoryTools.h"
struct little_map
{
    std::uintptr_t address;
    std::int64_t value;
};
int main(int argc, char *argv[])
{
    int Fitur = atoi(argv[1]);
    {
        char pkg[100];
        if (isapkrunning("com.tencent.ig") == 1)
        {
            sprintf(pkg, "com.tencent.ig");
        }
        else if (isapkrunning("com.vng.pubgmobile") == 1)
        {
            sprintf(pkg, "com.vng.pubgmobile");
        }
        else if (isapkrunning("com.pubg.krmobile") == 1)
        {
            sprintf(pkg, "com.pubg.krmobile");
        }
        else if (isapkrunning("com.rekoo.pubgm") == 1)
        {
            sprintf(pkg, "com.rekoo.pubgm");
        }

        char getRoot[100];
        if (getuid() == 0) {
            sprintf(getRoot, "MODE_ROOT");
        }
        else {
            sprintf(getRoot, "MODE_NO_ROOT");
        }

        initXMemoryTools(pkg, getRoot);
        switch (Fitur)
        {
        case 1:
            //FITUR
            break;
        case 2:
            //FITUR
            break;
        }
    }
}
