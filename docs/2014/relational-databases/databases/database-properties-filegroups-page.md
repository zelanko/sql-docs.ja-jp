---
title: '[データベースのプロパティ] ([ファイル グループ] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 45a83a7b3e8fe9af8280daca6a24a2686e97bf46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164330"
---
# <a name="database-properties-filegroups-page"></a>[データベースのプロパティ] \([ファイル グループ] ページ)
  このページを使用すると、ファイル グループを表示したり、選択したデータベースに新しいファイル グループを追加したりできます。 ファイル グループの種類は、 *Row* ファイル グループ、FILESTREAM データ、およびメモリ最適化ファイル グループに分けられます。  
  
 ROW ファイル グループには、通常のデータおよびログ ファイルが含まれます。 FILESTREAM データ ファイル グループには、FILESTREAM データ ファイルが含まれます。 これらのデータ ファイルには、FILESTREAM ストレージを使用する場合に、バイナリ ラージ オブジェクト (BLOB) データをファイル システムに対してどのように格納するかという情報が格納されます。 どちらのファイル グループもオプションは同じです。  
  
 FILESTREAM が有効になっていない場合、 **Filestream** のセクションは使用できません。 FILESTREAM ストレージを有効にするには、 [[サーバーのプロパティ] ([詳細設定] ページ)](../../database-engine/configure-windows/server-properties-advanced-page.md)を使用します。  
  
 ROW ファイル グループが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でどのように使用されるかについては、「[データベース ファイルとファイル グループ](database-files-and-filegroups.md)」を参照してください。 FILESTREAM データおよびファイル グループの詳細については、「[FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)」を参照してください。  
  
 データベースに 1 つ以上のメモリ最適化テーブルを含めるには、メモリ最適化ファイル グループが必要です。  
  
## <a name="row-and-filestream-data-filegroup-options"></a>ROW および FILESTREAM データ ファイル グループのオプション  
 **Name**  
 ファイル グループの名前を入力します。  
  
 **[ファイル]**  
 ファイル グループ内のファイルの数を表示します。  
  
 **読み取り専用です。**  
 ファイル グループを読み取り専用ステータスに設定します。  
  
 **[Default]**  
 このファイル グループを既定のファイル グループにします。 行と FILESTREAM データに対して、既定のファイル グループをそれぞれ 1 つずつ指定できます。  
  
 **[追加]**  
 データベースのファイル グループを一覧表示するグリッドに、新しい空の行を追加します。  
  
 **削除**  
 選択されたファイル グループ行をグリッドから削除します。  
  
## <a name="memory-optimized-data-filegroup-options"></a>メモリ最適化データ ファイル グループのオプション  
 **Name**  
 メモリ最適化ファイル グループの名前を入力します。  
  
 **[FILESTREAM ファイル]**  
 メモリ最適化データ ファイル グループのファイル (コンテナー) の数を表示します。 **[ファイル]** ページでコンテナーを追加することができます。  
  
 **[追加]**  
 データベースのファイル グループを一覧表示するグリッドに、新しい空の行を追加します。  
  
 **削除**  
 選択されたファイル グループ行をグリッドから削除します。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
