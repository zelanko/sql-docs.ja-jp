---
title: ProtocolDLL プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolDLL Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: fe8650d5-7b9d-46f8-bf74-baf1d9d2a06a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 31226e1a8e5c685dac971db1420d4ece489dfa02
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68040910"
---
# <a name="protocoldll-property-clientnetworkprotocol-class"></a>ProtocolDLL プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  によって指定されたネットワーク プロトコルに必要な .dll ファイルの名前を取得、 [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ClientNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)によって使用されるネットワーク プロトコルを表すオブジェクトを[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 クライアント ネットワーク プロトコルに必要なプロトコル .dll ファイルを指定する文字列値。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
