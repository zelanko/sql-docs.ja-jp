---
title: FileTable スキーマ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], table schema
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8515d78ddab2dd39e223087a44b0e021a5aca439
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179341"
---
# <a name="filetable-schema"></a>FileTable スキーマ
  FileTable の定義済みスキーマおよび固定スキーマについて説明します。  
  
|ファイル属性の名前|type|サイズ|既定|説明|ファイル システムのアクセシビリティ|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path_locator**|`hierarchyid`|変数 (variable)|A`hierarchyid`このアイテムの位置を識別します。|階層 FileNamespace 内でのこのノードの位置。<br /><br /> テーブルの主キーです。|Windows パス値を設定することによって作成および変更できます。|  
|**stream_id**|**[一意の ID] rowguidcol**||によって返される値、`NEWID()`関数。|FILESTREAM データの一意の ID。|該当なし。|  
|**file_stream**|`varbinary(max)`<br /><br /> `filestream`|変数 (variable)|NULL|FILESTREAM データが含まれています。|該当なし。|  
|**file_type**|`nvarchar(255)`|変数 (variable)|NULL。<br /><br /> ファイル システムの作成操作または名前変更操作によって、名前から取得されたファイル拡張子の値が格納されます。|ファイルの種類を表します。<br /><br /> この列は、フルテキスト インデックスの作成時に `TYPE COLUMN` として使用できます。<br /><br /> **file_type** は、保存される計算列です。|自動的に計算されます。 設定することはできません。|  
|**Name**|`nvarchar(255)`|変数 (variable)|GUID 値。|ファイルまたはディレクトリの名前。|Windows API を使用して作成または変更できます。|  
|**parent_path_locator**|`hierarchyid`|変数 (variable)|このアイテムが格納されているディレクトリを識別する `hierarchyid`|`hierarchyid`の格納されているディレクトリ。<br /><br /> **parent_path_locator** は、保存される計算列です。|自動的に計算されます。 設定することはできません。|  
|**cached_file_size**|`bigint`|||FILESTREAM データのサイズ (バイト単位)。<br /><br /> **cached_file_size** は、保存される計算列です。|キャッシュされたファイル サイズは自動的に最新の状態に維持されますが、特殊な状況で同期がとれなくなる場合があります。 正確なサイズを計算するには、使用、`DATALENGTH()`関数。|  
|**creation_time**|`datetime2(4)`<br /><br /> `not null`|8 バイト|現在の時刻|ファイルが作成された日付と時刻。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**last_write_time**|`datetime2(4)`<br /><br /> `not null`|8 バイト|現在の時刻|ファイルが最後に更新された日付と時刻。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**last_access_time**|`datetime2(4)`<br /><br /> `not null`|8 バイト|現在の時刻|ファイルが最後にアクセスされた日付と時刻。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_directory**|`bit`<br /><br /> `not null`|1 バイト|FALSE|行がディレクトリを表しているかどうかを示します。 この値は自動的に計算され、設定することはできません。|自動的に計算されます。 設定することはできません。|  
|**is_offline**|`bit`<br /><br /> `not null`|1 バイト|FALSE|オフライン ファイル属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_hidden**|`bit`<br /><br /> `not null`|1 バイト|FALSE|隠しファイル属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_readonly**|`bit`<br /><br /> `not null`|1 バイト|FALSE|読み取り専用ファイル属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_archive**|`bit`<br /><br /> `not null`|1 バイト|FALSE|アーカイブ属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_system**|`bit`<br /><br /> `not null`|1 バイト|FALSE|システム ファイル属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
|**is_temporary**|`bit`<br /><br /> `not null`|1 バイト|FALSE|一時ファイル属性。|自動的に計算されます。 Windows API を使用して設定することもできます。|  
  
## <a name="see-also"></a>参照  
 [FileTable の作成、変更、および削除](create-alter-and-drop-filetables.md)  
  
  