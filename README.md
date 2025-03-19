> [!IMPORTANT]  
> USE "menu.inc", O Menu com ALS Method ainda n�o foi concluido.

# FMenu (Vers�o Melhorada)
> Vers�o original dessa include: https://github.com/dinhkhoi2298/menu

# Modifica��es
> + Fun��o de gancho das keys pressionadas `KeyMenu:...(playerid, index)`
> + Fun��o OnMenuResponse foi substituida pelo macro `Menu:...(playerid, response, listitem)`
> + O Sistema agora � em base de strings n�o em menuid
> + Adicionado a possibilidade de colocar sub-item (do lado direito do menu)
> + Adicionado suporte a plataforma Android
> + Melhor organiza��o da Include
> + Adicionado a Documenta��o total da include
> + Foi adicionado textdraw-streamer para o melhor manuseio da include

## Todas as Fun��es
```bash
Menu_Add(playerid, const item[64], const item2[64] = "_")
Menu_Show(playerid, function, title, header)
Menu_Hide(playerid) 
Menu_SetColor(playerid, color)
Menu_ShowPage(playerid, page = 0) 
Menu_SelectIndex(playerid, index, cur_index = -1, bool:show = true) 
Menu_CurrentItem(playerid) 
Menu_GetMaxItemPerPage(playerid, cur_page) 
Menu_Showing(playerid) 
Menu_GetMaxPage(playerid) 
Selecionar(playerid, response)
ShowMiniMenu(playerid)
HideMiniMenu(playerid)
```

## Uso
```bash
CMD:teste(playerid)
{
    if(Menu_Showing(playerid))return 1;

	Menu_Add(playerid, "Corote","~g~R$350");
	Menu_Add(playerid, "Ypioca","~g~R$500");
	Menu_Add(playerid, "Sprunk","~g~R$50");
	Menu_SetColor(playerid, 0xFFFFFFFF);
	Menu_Show(playerid, MENU_COMPRAS_ALHAMBA, "Alhamba", "Menu de Compras");
    return 1;
}

KeyMenu:MENU_COMPRAS_ALHAMBA(playerid, index)
{
	switch(index)
	{
		case 0: //"Corote"
		{
			SetPlayerCameraPos(playerid, 501.959564, -22.952260, 1002.033569);
			SetPlayerCameraLookAt(playerid, 506.957946, -22.846529, 1002.103881, CAMERA_MOVE);
		}
		case 1: //"Ypioca"
		{
			SetPlayerCameraPos(playerid, 501.885833, -23.061210, 1001.059020);
			SetPlayerCameraLookAt(playerid, 506.851867, -22.854217, 1000.515197, CAMERA_MOVE);
		}
		case 2: //"sprunk"
		{
			SetPlayerCameraPos(playerid, 502.206542, -18.295412, 1001.397827);
			SetPlayerCameraLookAt(playerid, 505.349182, -14.705638, 999.902038, CAMERA_MOVE);
		}
	}
    return 1;
}

Menu:MENU_COMPRAS_ALHAMBA(playerid, response, listitem)
{
	if(response)
	{
		switch(listitem)
		{
			case 0: // corote 350
			{
				if(GetPlayerMoney(playerid) < 350)return SendClientMessage(playerid, -1, "<!> Voce nao tem todo esse dinheiro!");
				// ...
			}
			case 1: // ypioca 500
			{
				if(GetPlayerMoney(playerid) < 500)return SendClientMessage(playerid, -1, "<!> Voce nao tem todo esse dinheiro!");
				// ...
			}
			case 2: // spunk 50
			{
				if(GetPlayerMoney(playerid) < 50)return SendClientMessage(playerid, -1, "<!> Voce nao tem todo esse dinheiro!");
				// ...
			}
		}
	}
	else 
	{
		SetCameraBehindPlayer(playerid);
		Menu_Hide(playerid);
	}
	return 1;
}


```