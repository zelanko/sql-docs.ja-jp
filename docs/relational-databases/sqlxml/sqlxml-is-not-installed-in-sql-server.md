---
title: "SQL Server で SQLXML がインストールされていない |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee759b9c94f2bbc8a7f0c8cb1595600f29959a87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQL Server で SQLXML がインストールされない
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]前に[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、SQLXML 4.0 リリースされた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、すべての既定のインストールの一部であった[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外のバージョン[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]します。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、SQLXML の最新バージョン (SQLXML 4.0 SP1) が含まれないようになりました。 SQLXML 4.0 SP1 をインストールするからダウンロードして[SQLXML 4.0 SP1 のインストール場所](https://www.microsoft.com/en-us/download/details.aspx?id=30403)です。  
  
 アプリケーションを実行している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLXML 4.0 が必要とダウンロードし、SQLXML 4.0 SP1 をインストールする必要があります。  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>SQLOLEDB および SQL Server Native Client OLE DB プロバイダーを使用した場合の新しいデータ型による SQLXML 4.0 SP1 の動作  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]SQLXML を使用している開発者が使用することも、次のデータ型が導入されました。  
  
-   **[日付]**  
  
-   **[時刻]**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 SQLOLEDB で SQLXML 4.0 SP1 を使用する場合または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB から[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、これらの型は、開発者に文字列として表示されます。 SQLXML 4.0 SP1 では組み込みのスカラー型で使用する場合として、これら 4 つの新しいデータ型が有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider 11.0 以降。 SQLXML 4.0 SP1 をダウンロードしないと、これらの型を文字列以外の型にマッピングした場合、一部のデータが切り捨てられる可能性があります。 たとえば、マッピング**DateTime2**に**xsd:date**データに切り捨てられますが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** 3.33 ミリ秒の精度です。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 のプログラミング概念](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
