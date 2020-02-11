---
title: DataFactory のカスタマイズ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bdc406778bea0d6355e747998d2517b841fc17b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922776"
---
# <a name="datafactory-customization"></a>DataFactory のカスタマイズ
リモートデータサービス (RDS) を使用すると、3層のクライアント/サーバーシステムで簡単にデータアクセスを実行できます。 クライアントデータコントロールは、リモートデータソースに対してクエリを実行するための接続とコマンド文字列パラメーター、または更新を実行するための接続文字列および[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトパラメーターを指定します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 パラメーターは、リモートデータソースに対するデータアクセス操作を実行するサーバープログラムに渡されます。 RDS には、 [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクトと呼ばれる既定のサーバープログラムが用意されています。 **DataFactory**オブジェクトは、クエリによって生成されたすべての**レコードセット**オブジェクトをクライアントに返します。  
  
 ただし、RDSServer はクエリと更新の実行に制限されてい**ます。** 接続またはコマンド文字列に対して検証や処理を実行することはできません。  
  
 ADO では、 **DataFactory**が*ハンドラー*と呼ばれる別の種類のサーバープログラムと連携して動作するように指定できます。 ハンドラーは、データソースへのアクセスに使用する前に、クライアント接続とコマンド文字列を変更できます。 また、ハンドラーは、データソースに対するデータの読み取りおよび書き込みをクライアントが行う機能を制御するアクセス権を適用できます。  
  
 ハンドラーがクライアントパラメーターを変更するために使用するパラメーターとアクセス権は、カスタマイズファイルのセクションで指定されます。  
  
 次のトピックでは、 **DataFactory**オブジェクトのカスタマイズの詳細について説明します。  
  
-   [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [カスタマイズ ファイルの Connect セクション](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [カスタマイズ ファイルの SQL セクション](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [カスタマイズ ファイルの UserList セクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [カスタマイズ ファイルの Logs セクション](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [必要なクライアントの設定](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


