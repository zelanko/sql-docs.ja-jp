---
title: "DataFactory カスタマイズ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 044e738c69113740290843f14f0b2c14500307e1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="datafactory-customization"></a>DataFactory のカスタマイズ
リモート データ サービス (RDS) は、3 階層のクライアント/サーバー システムのデータ アクセスを簡単に実行する方法を提供します。 クライアントのデータ コントロールは、リモート データ ソース、または接続文字列でクエリを実行する接続とコマンドの文字列パラメーターを指定し、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの更新を実行するパラメーターです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 パラメーターは、リモート データ ソースに対してデータ アクセス操作が実行されるサーバーのプログラムに渡されます。 RDS と呼ばれる既定のサーバー プログラムの提供、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト。 **RDSServer.DataFactory**オブジェクトは、いずれかを返した**Recordset**クライアントへのクエリによって生成されるオブジェクト。  
  
 ただし、 **RDSServer.DataFactory**クエリと更新プログラムの実行に制限されます。 接続またはコマンド文字列での検証または処理は実行できません。  
  
 Ado を指定できます、 **DataFactory**職場と呼ばれるサーバー プログラムの別の型と組み合わせて、*ハンドラー*です。 ハンドラーには、データ ソースへのアクセスに使用されるようにクライアント接続とコマンド文字列を変更できます。 さらに、ハンドラーは、データ ソースにデータを読み書きするクライアントの権限を制御するアクセス権を適用できます。  
  
 ハンドラーは、クライアント パラメーターを変更し、アクセス権で使用されるパラメーターは、カスタマイズ ファイルのセクションで指定します。  
  
 次のトピックでは、カスタマイズの詳細について、 **DataFactory**オブジェクト。  
  
-   [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [カスタマイズ ファイルの Connect セクション](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [カスタマイズ ファイルの SQL セクション](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [カスタマイズ ファイルの UserList セクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [カスタマイズ ファイルの Logs セクション](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [必要なクライアントの設定](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



