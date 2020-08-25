---
description: エラー (ADO)
title: エラー (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 8ae6611b-3069-4155-b014-c0c9da37be39
author: rothja
ms.author: jroth
ms.openlocfilehash: 392d1f2fdfc0a7fe2e0cf9e1e14efb77f396acfd
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806123"
---
# <a name="errors-ado"></a>エラー (ADO)
ADO オブジェクトに関連する操作では、1つ以上のプロバイダーエラーが発生することがあります。 各エラーが発生すると、**接続**オブジェクトの**エラー**コレクションに1つまたは複数の**エラー**オブジェクトが配置されます。 ADO アプリケーションでの警告とエラーの処理の詳細については、「 [エラー処理](./error-handling.md)」を参照してください。  
  
 アプリケーションエラーは、別のメカニズムを使用して発生させることができます。 たとえば、Visual Basic では、 **Err** オブジェクトにアプリケーションレベルのエラーが含まれます。