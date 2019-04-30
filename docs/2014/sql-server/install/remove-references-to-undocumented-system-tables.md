---
title: 文書化されていないシステム テーブルへの参照の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c2c25120191b88abcf177723749aa5c46ba44ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294820"
---
# <a name="remove-references-to-undocumented-system-tables"></a>ドキュメントに記載されていないシステム テーブルへの参照の削除
  以前のリリースのドキュメントには記載されていなかった多くのシステム テーブルが変更されたか、存在しなくなりました。そのため、アップグレード後にそのようなシステム テーブルを使用すると、エラーが発生する場合があります。 アップグレード アドバイザーはシステム テーブル名への参照を検索するので、システム テーブルと同じ名前のユーザー テーブルへの参照を報告します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 ドキュメントに記載されていない以下のシステム テーブルは削除されました。  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>修正措置  
 次の表に従ってアプリケーションを修正してください。  
  
|以前のシステム ストアド プロシージャ|新しく使用する機能|  
|----------------|---------|  
|**sysfulltextnotify**|**TableFulltextPendingChanges** OBJECTPROPERTYEX 関数のプロパティ。|  
|**syslocks**|**sys.dm_tran_locks**動的管理ビューまたは sp_lock、または**sys.syslockinfo**互換性ビューです。|  
|**sysproperties**|**sys.extended_properties**カタログ ビューまたは**fn_listextendedproperty**関数|  
|**sysxlogins**|**sys.server_principals**カタログ ビューまたは**syslogins**互換性ビューです。|  
|すべて**spt _** テーブル|使用可能な交換はありません。|  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
