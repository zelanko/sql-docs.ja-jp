---
title: OLE DB スキーマ行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- schema rowsets [OLE DB]
- schema rowsets [Analysis Services], OLE DB
- OLE DB schema rowsets
- rowsets [Analysis Services], OLE DB
ms.assetid: ca2ee87a-ba04-4501-9125-33934c58ab31
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3a1d03d6fd8d527d48a9a4051f201368ff870882
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161193"
---
# <a name="ole-db-schema-rowsets"></a>OLE DB スキーマ行セット
  次の OLE DB スキーマ行セットは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされています。 使用して、`DISCOVER_ENUMERATORS`を含む行セット、 [Discover](../../xmla/xml-elements-methods-discover.md)特定のデータ ソース プロバイダーが行セットをサポートしているかどうかを確認する方法。  
  
 これらの行セットの詳細情報は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Web サイトの MSDN® ライブラリの OLE DB プログラマ向けリファレンスで「スキーマ行セット」のトピックを検索することによっても参照できます。  
  
 次の表では、このスキーマ行セットについて説明します。  
  
|[行セット]|説明|  
|------------|-----------------|  
|`DBSCHEMA_ASSERTIONS`|カタログで定義され、特定のユーザーによって所有されているアサーションを識別します。|  
|[DBSCHEMA_CATALOGS 行セット](dbschema-catalogs-rowset.md) <sup>1</sup>|データベース管理システム (DBMS) からアクセス可能なカタログに関連付けられている物理属性を識別します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access などの一部のシステムでは、カタログを 1 つしか指定できません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合、この行セットでは、システム データベースで定義されたすべてのカタログ (データベース) を列挙します。|  
|`DBSCHEMA_CHARACTER_SETS`|カタログで定義され、特定のユーザーがアクセスできる文字セットを識別します。|  
|`DBSCHEMA_CHECK_CONSTRAINTS`|カタログで定義され、特定のユーザーによって所有されているチェック制約を識別します。|  
|`DBSCHEMA_CHECK_CONSTRAINTS_BY_TABLE`|カタログで定義され、特定のユーザーによって所有されている特定のテーブルのチェック制約を識別します。|  
|`DBSCHEMA_COLLATIONS`|カタログで定義され、特定のユーザーがアクセスできる文字照合順序を識別します。|  
|`DBSCHEMA_COLUMN_DOMAIN_USAGE`|カタログで定義された列のうち、カタログで定義され、特定のユーザーによって所有されているドメインに依存するものを識別します。|  
|`DBSCHEMA_COLUMN_PRIVILEGES`|カタログで定義され、特定のユーザーによって使用または付与されるテーブル列の権限を識別します。|  
|[DBSCHEMA_COLUMNS 行セット](dbschema-columns-rowset.md) <sup>1</sup>|指定された制約条件を満たすすべての列の列情報を提供します。|  
|`DBSCHEMA_CONSTRAINT_COLUMN_USAGE`|参照制約、一意制約、チェック制約、およびアサーションによって使用される列のうち、カタログで定義され、特定のユーザーによって所有されているものを識別します。|  
|`DBSCHEMA_CONSTRAINT_TABLE_USAGE`|参照制約、一意制約、チェック制約、およびアサーションによって使用されるテーブルのうち、カタログで定義され、特定のユーザーによって所有されているものを識別します。|  
|`DBSCHEMA_FOREIGN_KEYS`|特定のユーザーによってカタログで定義されている外部キー列を識別します。 このスキーマ行セットは、SQL を使用しないプログラマの便宜を図って、複数の ISO スキーマ ビューに基づいて構築されています。 このスキーマ行セットがサポートされている場合は、関連する ISO ビュー (`REFERENTIAL_CONSTRAINTS` および `CONSTRAINT_COLUMN_USAGE`) と同期する必要があります。|  
|`DBSCHEMA_INDEXES`|カタログで定義され、特定のユーザーによって所有されているインデックスを識別します。|  
|`DBSCHEMA_KEY_COLUMN_USAGE`|カタログで定義され、特定のユーザーによってキーとして制約される列を識別します。|  
|`DBSCHEMA_PRIMARY_KEYS`|特定のユーザーによってカタログで定義されている主キー列を識別します。 このスキーマ行セットは、SQL を使用しないプログラマの便宜を図って、ISO スキーマ ビューに基づいて構築されています。 このスキーマ行セットがサポートされている場合は、関連する ISO ビュー (`CONSTRAINT_COLUMN_USAGE`) と同期する必要があります。|  
|`DBSCHEMA_PROCEDURE_COLUMNS`|プロシージャによって返される行セットの列に関する情報を返します。|  
|`DBSCHEMA_PROCEDURE_PARAMETERS`|プロシージャのパラメーターとリターン コードに関する情報を返します。|  
|`DBSCHEMA_PROCEDURES`|カタログで定義され、特定のユーザーによって所有されているプロシージャを識別します。 これは OLE DB の拡張機能です。|  
|[DBSCHEMA_PROVIDER_TYPES 行セット](dbschema-provider-types-rowset.md) <sup>1</sup>|データ プロバイダーによってサポートされている (基本) データ型を識別します。|  
|`DBSCHEMA_REFERENTIAL_CONSTRAINTS`|カタログで定義され、特定のユーザーによって所有されている参照制約を識別します。|  
|`DBSCHEMA_SCHEMATA`|特定のユーザーによって所有されているスキーマを識別します。|  
|`DBSCHEMA_SQL_LANGUAGES`|カタログで定義されたデータを処理する SQL 実装によってサポートされているレベル、オプション、および言語の準拠を識別します。|  
|`DBSCHEMA_STATISTICS`|カタログで定義され、特定のユーザーによって所有されている統計を識別します。<br /><br /> このテーブルは、`TABLE_STATISTICS` 行セットとは関係ありません。|  
|`DBSCHEMA_TABLE_CONSTRAINTS`|カタログで定義され、特定のユーザーによって所有されているテーブル制約を識別します。|  
|`DBSCHEMA_TABLE_PRIVILEGES`|カタログで定義され、特定のユーザーによって使用または付与されるテーブルの権限を識別します。|  
|`DBSCHEMA_TABLE_STATISTICS`|プロバイダーのテーブルで使用できる統計のセットについて記述します。<br /><br /> この行セットは、`STATISTICS` 行セットとは関係ありません。|  
|[DBSCHEMA_TABLES 行セット](dbschema-tables-rowset.md) <sup>1</sup>|メジャー グループおよびディメンション内のテーブルとして公開される識別[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。|  
|`DBSCHEMA_TABLES_INFO` <sup>1</sup>|カタログで定義され、特定のユーザーがアクセスできるテーブル (ビューも含む) を識別します。|  
|`DBSCHEMA_TRANSLATIONS`|カタログで定義され、特定のユーザーがアクセスできる文字変換を識別します。|  
|`DBSCHEMA_TRUSTEE`|データ ソースのトラスティを列挙します。|  
|`DBSCHEMA_USAGE_PRIVILEGES`|カタログで定義され、特定のユーザーによって使用または付与されるオブジェクトの `USAGE` 権限を識別します。|  
|`DBSCHEMA_VIEW_COLUMN_USAGE`|カタログで定義され、特定のユーザーがアクセスできるビューを識別します。|  
|`DBSCHEMA_VIEW_TABLE_USAGE`|カタログで定義され、特定のユーザーによって所有されている表示済みテーブルが依存するテーブルを識別します。|  
|`DBSCHEMA_VIEWS`|カタログで定義され、特定のユーザーがアクセスできるビューを識別します。|  
  
 <sup>1</sup>の MSOLAP データ ソース プロバイダーでサポートされているスキーマ行セットを示す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA プロバイダー。  
  
## <a name="see-also"></a>参照  
 [DISCOVER_ENUMERATORS 行セット](../xml/discover-enumerators-rowset.md)   
 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
