---
title: アセンブリに関する情報の取得 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e9940c597e176542fbfcbd7968ce96b496651f88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070960"
---
# <a name="getting-information-about-assemblies"></a>アセンブリについての情報の取得
  次のカタログ ビューや関数により、アセンブリに関するメタデータにクエリを行うことができます。  
  
 **個別のアセンブリに関する情報を取得するには**  
  
-   [ASSEMBLYPROPERTY &#40;TRANSACT-SQL&#41;](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 **データベース内のすべてのアセンブリに関する情報を取得するには**  
  
-   [sys.assemblies &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 **アセンブリに関する情報を取得するには、ファイル、アセンブリ バイナリを含むソース ファイル、およびファイルのデバッグ**  
  
-   [sys.assembly_files &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 **アセンブリ間の参照情報を取得するには**  
  
-   [sys.assembly_references &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 **ユーザー定義型に関するアセンブリ情報を取得するには**  
  
-   [sys.assembly_types &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 **ランタイム (CLR) ストアド プロシージャ、トリガー、および関数の共通言語に関するアセンブリ情報を取得するには**  
  
-   [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 **非 CLR オブジェクトに関する情報を取得するには**  
  
-   [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a>参照  
 [アセンブリ&#40;データベース エンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [アセンブリのデザイン](../../relational-databases/clr-integration/assemblies-designing.md)   
 [アセンブリの実装](assemblies-implementing.md)  
  
  
