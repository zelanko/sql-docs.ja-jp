---
title: "プロジェクトの設定 (型のマッピング) (SybaseToSQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 49a4391c9542ab57ed815dc2670bed997a10a064
ms.openlocfilehash: 87c5ee7f5c4ab77748b11677994eecc7e5575490
ms.contentlocale: ja-jp
ms.lasthandoff: 10/04/2017

---
# <a name="project-settings-type-mapping-sybasetosql"></a>プロジェクトの設定 (型のマッピング) (SybaseToSQL)
[型マッピング] ページ、**プロジェクト設定** ダイアログ ボックスには、SSMA に Sybase Adaptive Server Enterprise (ASE) データ型に変換する方法をカスタマイズする設定が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
型マッピング ページがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   今後のすべての SSMA プロジェクトの種類のマッピングの設定を指定する、**ツール**メニューの **プロジェクト設定の既定の**、設定は表示または変更に必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップダウンを選び、**型マッピング**左側のウィンドウの下部にあります。  
  
-   現在のプロジェクトの設定を指定する、**ツール**メニューの **プロジェクト設定**、し、**型マッピング**左側のウィンドウの下部にあります。  
  
## <a name="options"></a>オプション  
**変換元の型**  
マップされた ASE データ型。  
  
**ターゲットの種類**  
ターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ASE の指定したデータ型のデータ型。  
  
Sybase 型マッピングの既定 SSMA の次のセクションの表を参照してください。  
  
**[追加]**  
マッピングのリストに、データ型を追加する をクリックします。  
  
**[編集]**  
マッピングの一覧で選択したデータ型を編集する をクリックします。  
  
**[削除]**  
マッピングのリストから選択したデータ型のマッピングを削除する をクリックします。  
  
**既定値にリセット**  
SSMA の既定値に型マッピングのリストをリセットする をクリックします。  
  
## <a name="default-type-mapping"></a>既定の型マッピング  
次の表に、ASE 間の既定の型マッピングと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
|ASE データ型|SQL Server データ型|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**[バイナリ]**|**[バイナリ]**|  
|**バイナリ [\*..8000]**|**バイナリ [\*]**|  
|**バイナリ [8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char のさまざまな**|**varchar**|  
|**char のさまざまな [\*..8000]**|**varchar [\*]**|  
|**char のさまざまな [8001..\*]**|**varchar(max)**|  
|**char[\*..8000]**|**char[\*]**|  
|**char [8001..\*です]。**|**varchar(max)**|  
|**文字**|**char**|  
|**可変の文字**|**varchar**|  
|**文字がさまざまな [\*..8000]**|**varchar [\*]**|  
|**文字がさまざまな [8001..\*]**|**varchar(max)**|  
|**文字 [\*..8000]**|**char[\*]**|  
|**文字 [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2 [3]**|  
|**年 12 月**|**decimal**|  
|**dec[\*..\*]**|**decimal [\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**decimal [\*..\*]**|**decimal [\*]**|  
|**decimal [\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**倍精度**|**float [53]**|  
|**float**|**float [53]**|  
|**float [\*..15]**|**float [24]**|  
|**float [16\*]**|**float [53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**整数 (integer)**|**int**|  
|**longsysname**|**nvarchar [255]**|  
|**money**|**money**|  
|**national char**|**nchar**|  
|**national char [\*..4000]**|**nchar [\*]**|  
|**varying、national char**|**nvarchar**|  
|**varying、national char [\*..4000]**|**nvarchar [\*]**|  
|**varying、national char [4001..\*]**|**nvarchar(max)**|  
|**national char [4001..\*]**|**nvarchar(max)**|  
|**各国語文字**|**nchar**|  
|**各国語文字 [\*..4000]**|**nchar [\*]**|  
|**各国語文字 [4001..\*]**|**nvarchar(max)**|  
|**各国語文字 varying**|**nvarchar**|  
|**各国語文字 varying [\*..4000]**|**nvarchar [\*]**|  
|**各国語文字 varying [4001..\*]**|**nvarchar(max)**|  
|**各国語 varchar**|**nvarchar**|  
|**各国語 varchar [\*..4000]**|**nvarchar [\*]**|  
|**各国語 varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**nchar varying**|**nvarchar**|  
|**nchar varying [\*..4000]**|**nvarchar [\*]**|  
|**nchar varying [4001..\*]**|**nvarchar(max)**|  
|**nchar [\*..4000]**|**nchar [\*]**|  
|**nchar [4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**数値 [\*..\*]**|**数値 [\*]**|  
|**数値 [\*..\*][\*..\*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [\*..4000]**|**nvarchar [\*]**|  
|**nvarchar [4001..\*]**|**nvarchar(max)**|  
|**real**|**float [24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar [128]**|  
|**sysname [\*..\*]**|**nvarchar [255]**|  
|**text**|**text**|  
|**time**|**時間 [3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**unichar varying**|**nvarchar**|  
|**unichar varying [\*..4000]**|**nvarchar [\*]**|  
|**unichar varying [4001..\*]**|**nvarchar(max)**|  
|**unichar [\*..4000]**|**nchar [\*]**|  
|**unichar [4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [\*..4000]**|**nvarchar [\*]**|  
|**univarchar [4001..\*]**|**nvarchar(max)**|  
|**符号なしの bigint**|**数値 [20] [0]**|  
|**符号なし整数**|**bigint**|  
|**符号なし smallint**|**int**|  
|**符号なし tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*..8000]**|**varbinary [\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*..8000]**|**varchar [\*]**|  
|**varchar [8001..\*]**|**varchar(max)**|  
  

