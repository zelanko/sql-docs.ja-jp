---
title: sp_help_spatial_geometry_histogram (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_histogram
- sp_help_spatial_geometry_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_histogram
ms.assetid: 036aaf61-df3e-40f7-aa4e-62983c5a37bd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c29562bbdaeff69084547c3505fc84def3a0c668
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663237"
---
# <a name="sphelpspatialgeometryhistogram-transact-sql"></a>sp_help_spatial_geometry_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  空間インデックス用の境界ボックスとグリッドのパラメーターのキー設定を容易にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geometry_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @xmin = ] 'minx' ]   
     [ , [ @ymin = ] 'miny' ]   
     [ ,.[ @xmax = ] 'maxx' ]  
     [ , [ @ymax = ] 'maxy' ]  
     [ , [ @sample = ] 'sample' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tabname =**] **'***tabname $***'**  
 空間インデックスが指定されているテーブルの修飾名または非修飾名です。  
  
 引用符が必要なのは、修飾されたテーブルを指定する場合のみです。 データベース名を含む完全修飾名を指定する場合、データベース名は現在のデータベースの名前である必要があります。 *tabname $* は**sysname**、既定値はありません。  
  
 [  **@colname =** ] **'***colname***'**  
 指定されている空間列の名前です。 *colname*は、 **sysname**、既定値はありません。  
  
 [  **@resolution =** ] **'***解決***'**  
 境界ボックスの解像度です。 有効な値は 10 ～ 5000 です。 *解像度*は、 **tinyint**、既定値はありません。  
  
 [  **@xmin =** ] **'***xmin***'**  
 "X の最小値" 境界ボックス プロパティです。 *xmin*は、 **float**、既定値はありません。  
  
 [  **@ymin =** ] **'***ymin***'**  
 "Y の最小値" 境界ボックス プロパティです。 *ymin*は、 **float**、既定値はありません。  
  
 [  **@xmax =** ] **'***xmax***'**  
 "X の最大値" 境界ボックス プロパティです。 *xmax*は、 **float**、既定値はありません。  
  
 [  **@ymax =** ] **'***ymax***'**  
 "Y の最大値" 境界ボックス プロパティです。 *ymax*は、 **float**、既定値はありません。  
  
 [  **@sample =** ] **'***サンプル***'**  
 使用するテーブルの割合を指定します。 有効な値は、0 ～ 100 です。 *サンプル*は、 **float**します。 既定値は 100 です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 テーブルの値が返されます。 テーブルの列の内容を次の表に示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|各セルの一意な ID を表します。値は 1 から開始されます。|  
|**セル**|**geometry**|それぞれのセルを表す四角形です。 セルの形は、空間インデックス作成用に使用されたセルの形と同じです。|  
|**row_count**|**bigint**|セルに接しているかまたはセルを含む空間オブジェクトの数を示します。|  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーのメンバーである必要があります、**パブリック**ロール。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 SSMS 空間タブでは、結果がグラフィカルに表示されます。 空間ウィンドウに対して結果をクエリすることにより、結果アイテムの概算数を取得できます。 テーブル内のオブジェクトは 1 つ以上のセルをカバーしている場合があるため、セルの合計が実際のオブジェクトの数より大きくなることがあります。  
  
 境界ボックスの外部にあるオブジェクトまたは境界ボックスの境界に接しているオブジェクトの数を格納する追加の行が結果セットに追加される場合があります。 **Cellid** 0 は、この行の**セル**この行が含まれている、 **LineString**境界ボックスを表します。 この行は、境界ボックスの外部の領域全体を表します。  
  
## <a name="examples"></a>使用例  
 次の例は、サンプル テーブルを作成しを呼び出して**sp_help_spatial_geometry_histogram**テーブルにします。  
  
 `USE AdventureWorksDW2012`  
  
 `GO`  
  
 `-- Set database compatibility for circular arc segments`  
  
 `ALTER DATABASE AdventureWorksDW2012`  
  
 `SET COMPATIBILITY_LEVEL = 110;`  
  
 `GO`  
  
 `-- Create table to execute sp_help_spatial_geometry_histogram on`  
  
 `CREATE TABLE TownSites`  
  
 `(`  
  
 `Location geometry NULL,`  
  
 `SiteName nvarchar(50) NULL`  
  
 `)`  
  
 `GO`  
  
 `-- Insert site data into table`  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('POINT(0 0)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Booth Map';`  
  
 `SET @g = geometry::Parse('POLYGON((1 1, 1 2, 2 2, 2 1, 1 1))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Town Hall';`  
  
 `SET @g = geometry::Parse('CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-1 0, 0 -1, 1 0),(1 0, 1 2, -1 0)))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Park';`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(1 5, 2 2, 5 1)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Road';`  
  
 `-- Call proc to see data within bounding box`  
  
 `EXEC sp_help_spatial_geometry_histogram @tabname = TownSites, @colname = Location, @resolution = 64, @xmin = -2, @ymin = -2, @xmax = 3, @ymax = 3, @sample = 100;`  
  
 `GO`  
  
 `DROP TABLE TownSites;`  
  
 `GO`  
  
## <a name="see-also"></a>参照  
 [空間インデックス ストアド プロシージャ&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
