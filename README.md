#include <YSI\y_hooks>

enum E_PENAMBANG
{
    STREAMER_TAG_MAP_ICON:PENAMBANG
}
new PENAMBANGAREA[MAX_PLAYERS][E_PENAMBANG];

stock RefreshPenambang(playerid){
	if(PlayerData[playerid][pJob] == 3){
		PENAMBANGAREA[playerid][PENAMBANG] = CreateDynamicMapIcon(-2009.3083,-1513.9203,84.9326, 11, 0, -1, -1, playerid, 99999.0, MAPICON_GLOBAL);
        PENAMBANGAREA[playerid][PENAMBANG] = CreateDynamicMapIcon(-816.9091,-1967.1306,4.7209, 11, 0, -1, -1, playerid, 99999.0, MAPICON_GLOBAL);
        PENAMBANGAREA[playerid][PENAMBANG] = CreateDynamicMapIcon(2153.3420,-2268.9792,13.3074, 11, 0, -1, -1, playerid, 99999.0, MAPICON_GLOBAL);
	}
	return 1;
}

hook OnPlayerKeyStateChange(playerid, newkeys, oldkeys)
{
	if(IsPlayerConnected(playerid))
	{
		if(IsPlayerInRangeOfPoint(playerid, 1.0, -2009.3083,-1513.9203,84.9326))
    	{
        	if(PlayerData[playerid][pJob] == 3)
        	{
            	if(PlayerData[playerid][pMiner] == 0)
                {
                    PlayerData[playerid][pMiner] = 1;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
		if(IsPlayerInRangeOfPoint(playerid, 1.0, -2008.4796,-1525.7048,85.8075))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 1)
                {
                    PlayerData[playerid][pMiner] = 2;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                } 
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.4945,-1536.0189,86.5623))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 2)
                {
                    PlayerData[playerid][pMiner] = 3;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.7734,-1547.6605,87.3109))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 3)
                {
                    PlayerData[playerid][pMiner] = 4;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.5145,-1557.1511,88.5500))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 4)
                {
                    PlayerData[playerid][pMiner] = 5;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.5267,-1564.7582,88.4920))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 5)
                {
                    PlayerData[playerid][pMiner] = 6;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2010.0101,-1581.3101,88.0476))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(PlayerData[playerid][pMiner] == 6)
                {
                    PlayerData[playerid][pMiner] = 0;
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "AmbilBatu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 10.0, -816.9091,-1967.1306,4.7209))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(Inventory_Count(playerid, "Batu") < 1)
                    return Error(playerid, "Kamu tidak Batu!");
                {
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "Cuci Batu");
                }
            }
        }
        if(IsPlayerInRangeOfPoint(playerid, 10.0, 2153.3420,-2268.9792,13.3074))
        {
            if(PlayerData[playerid][pJob] == 3)
            {
                if(Inventory_Count(playerid, "Batu Cucian") < 1)
                    return Error(playerid, "Kamu tidak Batu Cucian!");
                {
                    matasatu(playerid);
                    PlayerTextDrawSetString(playerid, MATATD[playerid][2], "Olah Batu");
                }
            }
        }
	}
	return 1;
}

hook OnPlayerClickPlayerTD(playerid, PlayerText:playertextid){
    if(playertextid == MATATD[playerid][1]){
        if(IsPlayerInRangeOfPoint(playerid, 10.0, -816.9091,-1967.1306,4.7209))
        {
            ApplyAnimation(playerid, "BD_FIRE", "wash_up", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 20, "Cuci_Batu..", 1000, "miner1", 1687547311);
        }
        if(IsPlayerInRangeOfPoint(playerid, 10.0, 2153.3420,-2268.9792,13.3074))
        {
            ApplyAnimation(playerid, "BD_FIRE", "wash_up", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 20, "Cuci_Batu..", 1000, "miner2", 1687547311);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2009.3083,-1513.9203,84.9326))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2008.4796,-1525.7048,85.8075))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.4945,-1536.0189,86.5623))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.7734,-1547.6605,87.3109))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.5145,-1557.1511,88.5500))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2007.5267,-1564.7582,88.4920))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
        if(IsPlayerInRangeOfPoint(playerid, 1.0, -2010.0101,-1581.3101,88.0476))
        {
            ApplyAnimation(playerid, "BASEBALL", "Bat_M", 4.1, 1, 1, 1, 1, 0, 1);
            StartPlayerLoadingBar(playerid, 10, "Ambil_Batu..", 1000, "miner", 1687547311);
            SetPlayerAttachedObject(playerid, 9, 18635, 6, 0.021, 0.000, -0.037, 9.000, 0.000, 0.000, 1.0000, 1.0000, 1.0000, 0xFFFFFFFF, 0xFFFFFFFF);
        }
    }
    return 1;
}

FUNC::miner1(playerid){
    ClearAnimations(playerid, 1);
    Inventory_Add(playerid, "Batu Cucian", 2936, 1);
    Inventory_Remove(playerid, "Batu", 1);
    ShowItemBox(playerid, "Batu", "Remove_1 Pcs", 3929, 4);
    ShowItemBox(playerid, "Batu Cucian", "Add_1 Pcs", 2936, 4);
    RemovePlayerAttachedObject(playerid, 9);
    return 1;
}

FUNC::miner2(playerid){
    ClearAnimations(playerid, 1);
    Inventory_Add(playerid, "Emas", 19941, 1);
    Inventory_Remove(playerid, "Batu Cucian", 1);
    ShowItemBox(playerid, "Batu Cucian", "Remove_1 Pcs", 2936, 4);
    ShowItemBox(playerid, "Emas", "Add_1 Pcs", 19941, 4);
    RemovePlayerAttachedObject(playerid, 9);
    return 1;
}

FUNC::miner(playerid){
    ClearAnimations(playerid, 1); 
    RemovePlayerAttachedObject(playerid, 9);

    new rand = random(4);
	if(rand == 0){
        Inventory_Add(playerid, "Batu", 3929, 1);
        ShowItemBox(playerid, "Batu", "Add_1 Pcs", 3929, 4);
    }
    if(rand == 1){
        Inventory_Add(playerid, "Batu", 3929, 2);
        ShowItemBox(playerid, "Batu", "Add_2 Pcs", 3929, 4);
    }
    if(rand == 2){
        Inventory_Add(playerid, "Batu", 3929, 3);
        ShowItemBox(playerid, "Batu", "Add_3 Pcs", 3929, 4);
    }
    if(rand == 3){
        Inventory_Add(playerid, "Batu", 3929, 4);
        ShowItemBox(playerid, "Batu", "Add_4 Pcs", 3929, 4);
    }
    return 1;
}
