---
title: "よく寄せられる質問 (FAQ) Linux の ODBC および macOS |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aa835ce2bb9e35191d9c3056dad2f208445c361a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>よく寄せられる質問 (FAQ) ODBC Linux および macOS 用
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver for に関する質問に対する回答は、次のとおり[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Linux や macOS にします。
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問

**ドライバーで Linux または macOS 上の既存の ODBC アプリケーションの動作方法**  
コンパイルし、コンパイルと Linux またはその他のドライバーを使用して macOS 上で実行する ODBC アプリケーションを実行することができます。 
  
**のどの機能[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]はこのバージョンのドライバー サポートしますか?**

ODBC driver on Linux and macOS 内のすべてのサーバー機能をサポートしている[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]LocalDB を除きます。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポートされる機能を参照してください[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)です。  
  
**ドライバーは Kerberos 認証をサポートしますか。**  
可能。 既存の Kerberos 環境のセットアップがあればを使用してサーバーに接続できる必要があります、 `Trusted_Connection=Yes` DSN または接続文字列オプションです。 詳細については、次を参照してください。 [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md)です。  
  
**どの Unicode エンコードする必要があります、アプリケーションを使用しますか。**  
SQL_CHAR データには UTF-8、SQL_WCHAR データには UTF-16 を使用してください。  

**ダウンロードしてテストおよび評価のために、ドライバーを使用して実行できる ODBC サンプルはありますか。**

サンプルについては、「 [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux (Linux の ODBC ドライバーに既存の MSDN C++ ODBC サンプルを使用する)](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) 」を参照してください。 またこれは、macOS ODBC ドライバーに適用します。 

**Linux の ODBC ドライバーは、または macOS オープン ソースですか。**

Linux および macOS 上の ODBC ドライバーは、オープン ソース製品ではありません。  

## <a name="see-also"></a>参照
[Linux および macOS 上の SQL Server 用 Microsoft ODBC Driver をインストールします。](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

