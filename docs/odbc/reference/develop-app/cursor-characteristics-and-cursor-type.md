---
title: カーソルの特性とカーソルの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8354fdabf6830780ec2d128492c86cc1edd582ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301629"
---
# <a name="cursor-characteristics-and-cursor-type"></a>カーソルの特定とカーソルの種類
アプリケーションは、カーソルの種類 (前方専用、静的、キーセットドリブン、または動的) を指定する代わりに、カーソルの特性を指定できます。 これを行うには、アプリケーションは、ステートメント ハンドルにカーソルを開く前にカーソルのスクロール機能 (SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性を設定) と感度 (SQL_ATTR_CURSOR_SENSITIVITY ステートメント属性を設定) を選択します。 ドライバーは、最も効率的にアプリケーションが要求した特性を提供するカーソルの種類を選択します。  
  
 アプリケーションがステートメント属性SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_SCROLLABLE、SQL_ATTR_CURSOR_SENSITIVITY、またはSQL_ATTR_CURSOR_TYPEを設定するたびに、ドライバーは、この 4 つの属性セット内の他のステートメント属性に必要な変更を行い、値の一貫性を維持します。 その結果、アプリケーションがカーソル特性を指定すると、ドライバーは、この暗黙的な選択に基づいてカーソルの種類を示す属性を変更できます。アプリケーションが型を指定すると、ドライバーは、選択した型の特性と一致するように他の属性のいずれかを変更できます。 これらのステートメント属性の詳細については[、SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)関数の説明を参照してください。  
  
 カーソルの種類とカーソルの特性の両方を指定するステートメント属性を設定するアプリケーションは、アプリケーションの要件を満たすそのドライバーで使用できる最も効率的な方法ではないカーソルを取得するリスクを実行します。  
  
 ステートメント属性の暗黙的な設定は、次の規則に従う必要があることを除いて、ドライバーで定義されます。  
  
-   順方向専用カーソルはスクロールできません。SQL_ATTR_CURSOR_SCROLLABLEの定義[を参照してください](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)。  
  
-   無神経なカーソルは更新可能ではありません (したがって、同時実行は読み取り専用です)。これは、ISO SQL 標準の無神経カーソルの定義に基づいています。  
  
 したがって、ステートメント属性の暗黙的な設定は、次の表で説明されている場合に発生します。  
  
|アプリケーション・セット属性の|暗黙的に設定されるその他の属性|  
|-----------------------------------|-------------------------------------|  
|SQL_CONCUR_READ_ONLYにSQL_ATTR_CONCURRENCY|SQL_INSENSITIVEにSQL_ATTR_CURSOR_SENSITIVITY。|  
|SQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、またはSQL_CONCUR_VALUESにSQL_ATTR_CONCURRENCY|ドライバーで定義されているSQL_UNSPECIFIEDまたはSQL_SENSITIVEにSQL_ATTR_CURSOR_SENSITIVITYします。 無神経なカーソルは常に読み取り専用であるため、SQL_INSENSITIVEに設定することはできません。|  
|SQL_NONSCROLLABLEにSQL_ATTR_CURSOR_SCROLLABLE|SQL_CURSOR_FORWARD_ONLYにSQL_ATTR_CURSOR_TYPE|  
|SQL_SCROLLABLEにSQL_ATTR_CURSOR_SCROLLABLE|ドライバーによって指定されたSQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、またはSQL_CURSOR_DYNAMICにSQL_ATTR_CURSOR_TYPEします。 決してSQL_CURSOR_FORWARD_ONLYに設定されることはありません。|  
|SQL_INSENSITIVEにSQL_ATTR_CURSOR_SENSITIVITY|SQL_CONCUR_READ_ONLYにSQL_ATTR_CONCURRENCY。<br /><br /> SQL_CURSOR_STATICにSQL_ATTR_CURSOR_TYPEします。|  
|SQL_SENSITIVEにSQL_ATTR_CURSOR_SENSITIVITY|ドライバーで指定されたSQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、またはSQL_CONCUR_VALUESにSQL_ATTR_CONCURRENCYします。 SQL_CONCUR_READ_ONLYに設定されることはありません。<br /><br /> ドライバーによって指定されたSQL_CURSOR_FORWARD_ONLY、SQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、またはSQL_CURSOR_DYNAMICにSQL_ATTR_CURSOR_TYPEします。|  
|SQL_UNSPECIFIEDにSQL_ATTR_CURSOR_SENSITIVITY|ドライバーによって指定されたSQL_CONCUR_READ_ONLY、SQL_CONCUR_LOCK、SQL_CONCUR_ROWVER、またはSQL_CONCUR_VALUESにSQL_ATTR_CONCURRENCYします。<br /><br /> ドライバーによって指定されたSQL_CURSOR_FORWARD_ONLY、SQL_CURSOR_STATIC、SQL_CURSOR_KEYSET_DRIVEN、またはSQL_CURSOR_DYNAMICにSQL_ATTR_CURSOR_TYPEします。|  
|SQL_CURSOR_DYNAMICにSQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLEにSQL_ATTR_SCROLLABLE。<br /><br /> SQL_SENSITIVEにSQL_ATTR_CURSOR_SENSITIVITY。 (しかし、SQL_ATTR_CONCURRENCYがSQL_CONCUR_READ_ONLYに等しくない場合にのみ。 更新可能な動的カーソルは、独自のトランザクションで行われた変更に対して常に影響を受けます。|  
|SQL_CURSOR_FORWARD_ONLYにSQL_ATTR_CURSOR_TYPE|SQL_NONSCROLLABLEにSQL_ATTR_CURSOR_SCROLLABLE。|  
|SQL_CURSOR_KEYSET_DRIVENにSQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLEにSQL_ATTR_SCROLLABLE。<br /><br /> SQL_UNSPECIFIEDまたはSQL_SENSITIVEにSQL_ATTR_SENSITIVITYします (SQL_ATTR_CONCURRENCYがSQL_CONCUR_READ_ONLYでない場合は、ドライバー定義の基準に従います)。|  
|SQL_CURSOR_STATICにSQL_ATTR_CURSOR_TYPE|SQL_SCROLLABLEにSQL_ATTR_SCROLLABLE。<br /><br /> SQL_INSENSITIVEにSQL_ATTR_SENSITIVITYします (SQL_ATTR_CONCURRENCYがSQL_CONCUR_READ_ONLYの場合)。<br /><br /> SQL_UNSPECIFIEDまたはSQL_SENSITIVEにSQL_ATTR_SENSITIVITYします (SQL_ATTR_CONCURRENCYがSQL_CONCUR_READ_ONLYでない場合)。|
