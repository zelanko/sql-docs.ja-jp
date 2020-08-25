---
description: カスタマイズ ファイルの Logs セクション
title: カスタマイズファイルログセクション |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: rothja
ms.author: jroth
ms.openlocfilehash: f478a1e1c18e9182d2effe77d37c0c329ba22c54
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759836"
---
# <a name="customization-file-logs-section"></a>カスタマイズ ファイルの Logs セクション
**Logs**セクションには、 **DataFactory**の操作中にエラーを記録するファイルの名前を指定する、ログファイルのエントリが含まれています。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
 ログファイルのエントリの形式は次のとおりです。  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>解説  
  
|パーツ|説明|  
|----------|-----------------|  
|**警戒**|これがログファイルエントリであることを示すリテラル文字列。|  
|*FileName*|完全なパスとファイル名。 一般的なファイル名は **c:\msdfmap.log**です。|  
  
 ログファイルには、各エラーのユーザー名、HRESULT、日付、時刻が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [カスタマイズファイルの接続セクション](./customization-file-connect-section.md)   
 [カスタマイズファイル SQL セクション](./customization-file-sql-section.md)   
 [カスタマイズファイルの UserList セクション](./customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](./datafactory-customization.md)   
 [必要なクライアント設定](./required-client-settings.md)   
 [カスタマイズファイルについて](./understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](./writing-your-own-customized-handler.md)