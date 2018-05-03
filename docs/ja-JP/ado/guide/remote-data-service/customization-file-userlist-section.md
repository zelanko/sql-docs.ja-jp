---
title: カスタマイズ ファイル UserList セクション |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b02ce717e303c039fe10889749fd0bc0c2e9b13
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="customization-file-userlist-section"></a>カスタマイズ ファイル UserList に関するセクション
**Userlist**に関連するセクション、**接続**セクションを同じセクションで*識別子*パラメーター。  
  
 このセクションに含めることができます、*ユーザー アクセス エントリ*、指定したユーザーの権限のアクセスを指定して上書き、*既定**エントリにアクセス*照合に**接続**セクションです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 ユーザー アクセス エントリの形式では。  
  
 *userName* **=**   
 ***accessRights***  
  
|要素|Description|  
|----------|-----------------|  
|*userName*|*ユーザー名*のこの接続を使用しているユーザーです。 IIS で有効なユーザー名が確立されている**Service Manager**ダイアログ。|  
|***accessRights***|次のアクセス権のいずれか。<br /><br /> -   **NoAccess** -ユーザーがデータ ソースにアクセスできません。<br />-   **読み取り専用**-ユーザーは、データ ソースを読み取ることができます。<br />-   **ReadWrite** : ユーザーの読み取りまたはデータ ソースに書き込むことができます。|  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイルのセクションを接続します。](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル ログ](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズ ファイル SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


