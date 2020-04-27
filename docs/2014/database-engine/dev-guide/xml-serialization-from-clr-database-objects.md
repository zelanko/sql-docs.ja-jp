---
title: CLR データベースオブジェクトからの XML シリアル化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 646d15dc3091323e6e7db2af757640122fb2f0fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62779781"
---
# <a name="xml-serialization-from-clr-database-objects"></a>CLR データベース オブジェクトからの XML シリアル化
  XML シリアル化は、次の 2 つのシナリオで必要になります。  
  
-   CLR (共通言語ランタイム) オブジェクトから Web サービスを呼び出す場合。  
  
-   UDT (ユーザー定義型) を XML に変換する場合。  
  
 `XmlSerializer` クラスを呼び出して XML シリアル化を実行すると、通常、新たにシリアル化アセンブリが生成され、シリアル化の基になるアセンブリを含むプロジェクトにオーバーロードされます。 ただし、セキュリティ上の理由から、CLR ではこのオーバーロードが無効になります。 したがって、web サービスを呼び出したり、内[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の UDT から XML への変換を実行したりするには、必要なシリアル化アセンブリを生成する .NET Framework に用意されている**Sgen**というツールを使用して、アセンブリを手動で作成する必要があります。 `XmlSerializer` を呼び出す場合は、次の手順に従って、シリアル化アセンブリを手動で作成する必要があります。  
  
1.  .NET Framework SDK に付属している**Sgen**ツールを実行して、ソースアセンブリの XML シリアライザーを含むアセンブリを作成します。  
  
2.  `CREATE ASSEMBLY` ステートメントを使用して、生成したアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録します。  
  
 XML シリアル化の実行時に発生する可能性があるエラーの詳細については、 [「動的に生成されたシリアル化アセンブリを読み込むことができません」](https://support.microsoft.com/kb/913668)という Microsoft サポートの記事を参照してください。  
  
 XMLSerializer でサポートされないデータ型については、.NET Framework のドキュメントで、.NET Framework の XML スキーマ バインディング サポートに関する情報を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR データベースオブジェクトからのデータアクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
