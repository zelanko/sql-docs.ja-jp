---
title: Enabled プロパティ (ServerNetworkProtocolIpAddress クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Enabled Property (ServerNetworkProtocolIpAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Enabled property
ms.assetid: 870fd4d0-6c77-462a-b480-d42eb044b2e7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f84a2c554ae14eb7a99a092d4821b6672f8eee7c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059834"
---
# <a name="enabled-property-servernetworkprotocolipaddress-class"></a>Enabled プロパティ (ServerNetworkProtocolIpAddress クラス)
  IP アドレスが有効かどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.Enabled [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンス上のネットワークプロトコルの IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](servernetworkprotocolipaddress-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 IP アドレスが有効かどうかを指定するブール値。IP アドレスが有効な場合は `true`、IP アドレスが無効な場合は `false` です。  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
