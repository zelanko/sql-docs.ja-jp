---
title: セーフモードまたは無制限モード用に DataFactory を構成する |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 92e3b029d2b18065faf50dcd0343f64b7b01654e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922940"
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>安全または無制限モード用の DataFactory の構成
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 既定では、ADO は "安全な" [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)構成と共にインストールされます。 RDS サーバーコンポーネントのセーフモードは、次の条件を満たしていることを意味します。  
  
1.  RDSServer にはハンドラーが必要です (これはレジストリキーの設定によって必須です)。  
  
2.  既定のハンドラーである msdfmap. handler が登録され、セーフハンドラーの一覧に存在し、既定のハンドラーとしてマークされます。  
  
3.  Msdfmap .ini ファイルは、Windows ディレクトリにインストールされます。 3層モードで RDS を使用する前に、必要に応じてこのファイルを構成する必要があります。  
  
 必要に応じて、無制限の**DataFactory**インストールを構成できます。 **DataFactory**は、カスタムハンドラーなしで直接使用できます。 ユーザーは接続文字列を変更することによってカスタムハンドラーを引き続き使用できますが、必須ではありません。 **RDSServer**オブジェクトを使用した場合の影響の詳細については、「 [RDS アプリケーションのセキュリティ保護](../../../ado/guide/remote-data-service/securing-rds-applications.md)」を参照してください。  
  
 セキュリティで保護された構成のハンドラーレジストリエントリを設定するレジストリファイルが提供されています。 セーフモードで実行するには、「」を実行します。  
  
 セキュリティの保護を実行した後、コマンドプロンプトウィンドウで「NET STOP W3SVC」と「NET START W3SVC」と入力して、Web サーバー上の World Wide Web 公開サービスを停止し、再起動する必要があります。  
  
## <a name="see-also"></a>参照  
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



