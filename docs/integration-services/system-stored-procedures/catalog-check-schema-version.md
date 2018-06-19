---
title: catalog.check_schema_version | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 69e47e57b6732fa5c616c9ef2ddf165d394ddd14
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331856"
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SSISDB カタログ スキーマと [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] バイナリ (ISServerExec および SQLCLR アセンブリ) に互換性があるかどうかを示します。  
  
 スキーマとバイナリに互換性がない場合、ISServerExec.exc でエラー メッセージが記録されます。  
  
 SSISDB スキーマのバージョンは、修正プログラムや更新プログラムの適用時にスキーマが変更された場合に増加します。 SSISDB バックアップの復元後にこのストアド プロシージャを実行して、スキーマとバイナリに互換性があるようにすることをお勧めします。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>引数  
 [ @use32bitruntime= ] *use32bitruntime*  
 パラメーターが **True** の場合、32 ビット バージョンの dtexec が呼び出されます。 *use32bitruntime* は、**Bool** です。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限が必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ。  
  
  
