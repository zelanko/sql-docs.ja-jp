---
description: プロジェクトの設定 (型のマッピング) (「」)
title: プロジェクトの設定 (型のマッピング) (「」)Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 48054f25a5c7156a6d9d25d4770d19437d9dbadf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454305"
---
# <a name="project-settings-type-mapping-accesstosql"></a>プロジェクトの設定 (型のマッピング) (「」)
型マッピングプロジェクトの設定を使用すると、SSMA プロジェクトの既定の型マッピングを設定できます。 個々のデータベースオブジェクトに対して、型マッピングを指定することもできます。 詳細については、「 [ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)」を参照してください。  
  
型マッピングは、[ **プロジェクトの設定** ] ダイアログボックスと [既定の **プロジェクトの設定** ] ダイアログボックスで使用できます。  
  
-   [ **プロジェクトの設定** ] ダイアログボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 型マッピングの設定にアクセスするには、[ **ツール** ] メニューの [ **プロジェクトの設定**] をクリックし、左ペインの [ **型マッピング** ] をクリックします。  
  
-   [ **既定のプロジェクトの設定** ] ダイアログボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 型マッピングの設定にアクセスするには、[ **ツール** ] メニューの [ **既定のプロジェクト設定**] をクリックし、[移行 **先のバージョン** ] ドロップダウンから表示/変更が必要な設定を選択して、左側のウィンドウの [種類の **マッピング** ] をクリックします。  
  
## <a name="options"></a>オプション  
**ソースの種類**  
マップするアクセスデータ型。  
  
**ターゲットの種類**  
指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] た Access データ型のターゲットまたは SQL Azure データ型。  
  
次の表は、ソースとターゲットのデータ型の既定のマッピングを示しています。  
  
|Access データ型|SQL Server データ型|  
|--------------------|------------------------|  
|**バイナリ [ \* .. \* ]**|**varbinary [ \* ]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**貨**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**メモ (memo)**|**nvarchar(max)**|  
|**memo** -Access 97|**varchar(max)**|  
|**single**|**real**|  
|**テキスト [ \* .. \* ]**|**nvarchar [ \* ]**|  
|**テキスト [ \* .. \* ]** -アクセス97用|**varchar [ \* ]**|  
  
**追加**  
[マッピング] ボックスの一覧にデータ型を追加する場合にクリックします。  
  
**[編集]**  
[マッピング] ボックスの一覧でデータ型を編集する場合にクリックします。  
  
**Remove**  
クリックすると、選択したデータ型マッピングが [マッピング] ボックスの一覧から削除されます。  
  
**既定値にリセット**  
すべてのデータ型マッピングを SSMA の既定値にリセットする場合にクリックします。  
  
## <a name="see-also"></a>参照  
[ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)  
[ユーザーインターフェイスリファレンス (アクセス)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
