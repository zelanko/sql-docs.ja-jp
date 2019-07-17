---
title: SQL Server で SQLXML がインストールされていない |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2adac1703facccda712db1e3f5826f784c0be141
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135324"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQL Server で SQLXML がインストールされない
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンでは、SQLXML 4.0 は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属してリリースされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバージョン ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] を除く) の既定のインストールに含まれていました。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、SQLXML の最新バージョン (SQLXML 4.0 SP1) が含まれないようになりました。 SQLXML 4.0 SP1 をインストールするダウンロードから[SQLXML 4.0 SP1 のインストール場所](https://www.microsoft.com/download/details.aspx?id=30403)します。  
  
 アプリケーションを実行している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLXML 4.0 を必要と SQLXML 4.0 SP1 ダウンロードしてインストールする必要があります。  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>SQLOLEDB および SQL Server Native Client OLE DB プロバイダーを使用した場合の新しいデータ型による SQLXML 4.0 SP1 の動作  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SQLXML を使用して開発者が使用することも、次のデータ型が導入されています。  
  
-   **Date**  
  
-   **時刻**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 SQLOLEDB の SQLXML 4.0 SP1 を使用する場合または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB から[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、これらの型が開発者に文字列として表示されます。 SQLXML 4.0 SP1 では組み込みのスカラー型で使用する場合として、これら 4 つの新しいデータ型が有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider 11.0 以降。 SQLXML 4.0 SP1 をダウンロードしないと、これらの型を文字列以外の型にマッピングした場合、一部のデータが切り捨てられる可能性があります。 たとえば、マッピング**DateTime2**に**xsd:date**によりデータに切り捨てられますが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** 3.33 ミリ秒の精度。  
  
## <a name="see-also"></a>関連項目  
 [SQLXML 4.0 のプログラミング概念](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
