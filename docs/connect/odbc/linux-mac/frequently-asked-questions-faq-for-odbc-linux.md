---
title: ODBC Linux と macOS のよく寄せられる質問 (FAQ)
description: Linux と macOS の Microsoft ODBC Driver for SQL Server に関する一般的な質問に対する回答を示します。
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700c89b520cdaa33a60f1adabe69c669388bcccb
ms.sourcegitcommit: fb1430aedbb91b55b92f07934e9b9bdfbbd2b0c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82886456"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>ODBC Linux と macOS のよく寄せられる質問 (FAQ)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

次に、ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Linux および macOS に関する質問に対する回答を示します。
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問

**Linux または macOS 上の既存の ODBC アプリケーションは、どのようにドライバーと連動しますか?**  
他のドライバーを使用して Linux または macOS 上でコンパイルして実行している ODBC アプリケーションは、コンパイルして実行することができます。 
  
**このバージョンのドライバーがサポートしている [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の機能はどれですか?**

ODBC Driver on Linux および macOS は、LocalDB を除く [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] のすべてのサーバー機能をサポートしています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のサポートされている機能について詳しくは、「[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)」をご覧ください。  
  
**ドライバーは Kerberos 認証をサポートしますか?**  
はい。 Kerberos 環境が既にセットアップされている場合は、`Trusted_Connection=Yes` DSN または接続文字列オプションを使用して、サーバーに接続できます。 詳細については、「[統合認証を使用する](../../../connect/odbc/linux-mac/using-integrated-authentication.md)」を参照してください。  
  
**アプリケーションではどの Unicode エンコードを使用すればよいですか?**  
SQL_CHAR データには UTF-8、SQL_WCHAR データには UTF-16 を使用してください。 システムのロケールとドライバーのバージョンによっては、複数のエンコードのいずれかを使用する UTF-8 以外のデータも、サポートされている可能性があります。 詳しくは、「[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)」をご覧ください。

**ドライバーの試用および評価のために、ダウンロードしてドライバーで実行できる ODBC サンプルはありますか?**

サンプルについては、「 [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux (Linux の ODBC ドライバーに既存の MSDN C++ ODBC サンプルを使用する)](/archive/blogs/sqlblog/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver) 」を参照してください。 これは macOS ODBC ドライバーにも当てはまります。

**Linux または macOS 上の ODBC ドライバーはオープンソースですか?**

いいえ、Linux および macOS 上の ODBC ドライバーは、オープンソース製品ではありません。  

## <a name="see-also"></a>参照

- [Linux に SQL Server 用 Microsoft ODBC Driver をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [macOS に Microsoft ODBC Driver for SQL Server をインストールする](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
