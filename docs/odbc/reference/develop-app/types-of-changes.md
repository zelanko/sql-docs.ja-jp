---
title: 変更の種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f44adb59aa9b0f25475a76a97fe3670de0228c08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301607"
---
# <a name="types-of-changes"></a>変更の種類
ODBC *3.x* (および任意のバージョンの ODBC) では、3 種類の変更が行われます。 これらの各機能は、下位互換性に異なる影響を与え、異なる方法で処理されます。 これらの変更点を次の表に示します。  
  
|変更の種類|説明|  
|--------------------|-----------------|  
|新機能|これらは、ODBC *3.x*の新機能であり、たとえば、行外のバインディングや記述子などです。 これらは、アプリケーションとドライバー、およびドライバー マネージャーがバージョン*3.x*の場合にのみ実装されるため、下位互換性を持たないようにします。|  
|重複した機能|これらは ODBC *2.x*と ODBC *3.x*に存在する機能ですが、それぞれに異なる方法で実装されています。 関数**の一****例です。** これらの機能と他の重複した機能の下位互換性の問題は、主にドライバー マネージャーでのマッピングによって処理されます。|  
|動作の変更|ODBC 2.x および ODBC *3.x*では*3.x*、これらの機能は異なる方法で処理されます。 日時 **#define**は一例です。 これらの機能は、ODBC *3.x*ドライバが、環境属性の設定に基づいて処理します。 (詳細については[、「動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)」を参照してください)。|
