---
title: SQLXML が SQL Server | にインストールされていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8fe1d4b937e5972eb90e567ded91f7a23af577d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012158"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQL Server で SQLXML がインストールされない
  
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンでは、SQLXML 4.0 は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属してリリースされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバージョン ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] を除く) の既定のインストールに含まれていました。 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、SQLXML の最新バージョン (SQLXML 4.0 SP1) が含まれないようになりました。 SQLXML 4.0 SP1 が使用可能な場合にインストールするには、 [SQLXML sp1 のインストール場所](https://www.microsoft.com/download/details.aspx?id=16978)からダウンロードします。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行されるアプリケーションに SQLXML 4.0 が必要な場合、およびコンピューターに [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] がインストールされていない場合は、SQLXML 4.0 SP1 をダウンロードしてインストールする必要があります。  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>SQLOLEDB および SQL Server Native Client OLE DB プロバイダーを使用した場合の新しいデータ型による SQLXML 4.0 SP1 の動作  
 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] では、SQLXML を利用する開発者が使用できる、次のデータ型が導入されています。  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 (Windows Data Access Components、以前の Microsoft Data Access Components の) SQLOLEDB または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降の [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Native Client OLE DB と共に SQLXML 4.0 SP1 を使用する場合、これらの新しいデータ型は文字列として表示されます。 SQLXML 4.0 SP1 を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0 と共に使用した場合、この 4 つの新しいデータ型は組み込みスカラー型として有効になります。 SQLXML 4.0 SP1 をダウンロードしないと、これらの型を文字列以外の型にマッピングした場合、一部のデータが切り捨てられる可能性があります。 たとえば、にマッピング`DateTime2`する`xsd:date`と、データが3.33 ミリ秒の[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime`有効桁数に切り捨てられます。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 のプログラミング概念](sqlxml-4-0-programming-concepts.md)  
  
  
