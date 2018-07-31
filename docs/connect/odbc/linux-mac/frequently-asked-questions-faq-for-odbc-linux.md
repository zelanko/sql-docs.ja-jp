---
title: ODBC Linux と macOS のよく寄せられる質問 (FAQ) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17d25f6084e136736dbc4c8a8ff3cb019ce4692e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991374"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>ODBC Linux と macOS のよく寄せられる質問 (FAQ)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

次に、ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] on Linux および macOS に関する質問に対する回答を示します。
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問

**Linux または macOS 上の既存の ODBC アプリケーションは、どのようにドライバーと連動しますか?**  
他のドライバーを使用して Linux または macOS 上でコンパイルして実行している ODBC アプリケーションは、コンパイルして実行することができます。 
  
**このバージョンのドライバーがサポートしている [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] の機能はどれですか?**

ODBC Driver on Linux および macOS は、LocalDB を除く [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] のすべてのサーバー機能をサポートしています。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポートについては、「 [Programming Guidelines](../../../connect/odbc/linux-mac/programming-guidelines.md)します。  
  
**ドライバーは Kerberos 認証をサポートしますか?**  
可能。 既存の Kerberos 環境のセットアップがあればを使用してサーバーに接続できる必要があります、 `Trusted_Connection=Yes` DSN または接続文字列オプションです。 詳細については、「[統合認証を使用する](../../../connect/odbc/linux-mac/using-integrated-authentication.md)」を参照してください。  
  
**アプリケーションではどの Unicode エンコードを使用すればよいですか?**  
SQL_CHAR データには UTF-8、SQL_WCHAR データには UTF-16 を使用してください。  

**ドライバーの試用および評価のために、ダウンロードしてドライバーで実行できる ODBC サンプルはありますか?**

サンプルについては、「 [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux (Linux の ODBC ドライバーに既存の MSDN C++ ODBC サンプルを使用する)](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) 」を参照してください。 またこれは、macOS の ODBC ドライバーに当てはまります。 

**Linux で ODBC ドライバーは、または macOS のオープン ソースですか。**

Linux と macOS の ODBC ドライバーはオープン ソース製品ではありません。  

## <a name="see-also"></a>参照
[Linux および macOS に Microsoft ODBC Driver for SQL Server をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
