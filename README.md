function SearchWrite(Search, Write, Type) gg.clearResults() gg.setVisible(false) gg.searchNumber(Search[1][1], Type) local count = gg.getResultCount() local result = gg.getResults(count) gg.clearResults() local data = {} local base = Search[1][2] if (count > 0) then for i, v in ipairs(result) do v.isUseful = true end for k=2, #Search do local tmp = {} local offset = Search[k][2] - base local num = Search[k][1] for i, v in ipairs(result) do tmp[#tmp+1] = {} tmp[#tmp].address = v.address + offset tmp[#tmp].flags = v.flags end tmp = gg.getValues(tmp) for i, v in ipairs(tmp) do if ( tostring(v.value) ~= tostring(num) ) then result[i].isUseful = false end end end for i, v in ipairs(result) do if (v.isUseful) then data[#data+1] = v.address end end if (#data > 0) then gg.toast("搜索到"..#data.."条数据") local t = {} local base = Search[1][2] for i=1, #data do for k, w in ipairs(Write) do offset = w[2] - base t[#t+1] = {} t[#t].address = data[i] + offset t[#t].flags = Type t[#t].value = w[1] if (w[3] == true) then local item = {} item[#item+1] = t[#t] item[#item].freeze = true gg.addListItems(item) end end end gg.setValues(t) else gg.toast("带镜路", false) return false end else gg.toast("带镜路") return false end end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) xgsl = xgsl + 1 end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) xgjg = true end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "" .. xgsl .. "") else gg.toast(qmnb[2]["name"] .. "") end end end end
function edit(orig,ret)_om=orig[1].memory or orig[1][1]_ov=orig[3].value or orig[3][1]_on=orig[2].name or orig[2][1]gg.clearResults()gg.setRanges(_om)gg.searchNumber(_ov,orig[3].type or orig[3][2])sz=gg.getResultCount()if sz<1 then gg.toast(_on.."搜索到")else sl=gg.getResults(720)for i=1,sz do ist=true for v=4,#orig do if ist==true and sl[i].value==_ov then cd={{}}cd[1].address=sl[i].address+(orig[v].offset or orig[v][2])cd[1].flags=orig[v].type or orig[v][3]szpy=gg.getValues(cd)cdlv=orig[v].lv or orig[v][1]cdv=szpy[1].value if cdlv==cdv then pdjg=true ist=true else pdjg=false ist=false end end end if pdjg==true then szpy=sl[i].address for x=1,#(ret)do xgpy=szpy+(ret[x].offset or ret[x][2])xglx=ret[x].type or ret[x][3]xgsz=ret[x].value or ret[x][1]xgdj=ret[x].freeze or ret[x][4]xgsj={{address=xgpy,flags=xglx,value=xgsz}}if xgdj==true then xgsj[1].freeze=xgdj gg.addListItems(xgsj)else gg.setValues(xgsj)end end xgjg=true end end if xgjg==true then gg.toast(_on.."搜索到")else gg.toast(_on.."搜索到")end end end
local jldz={}function KYXG(DZ,XGSJ,GNM,JLDZ)local t={}for i=1,#DZ do for k,w in ipairs(XGSJ) do offset=w[1]*4 t[#t+1]={}t[#t].address=DZ[i]+offset t[#t].flags=w[2]t[#t].value=w[3]if(w[4]==true)then local item={}item[#item+1]=t[#t]item[#item].freeze=true gg.addListItems(item)end end end gg.setValues(t)gg.toast(GNM.."")end function KY_ZZ(NCLX,SSSJ,XGSJ,GNM)gg.setVisible(false)if jldz[NCLX[4]]==nil then gg.clearResults()gg.setRanges(NCLX[1])gg.searchNumber(NCLX[2],NCLX[3])local count=gg.getResultCount()local result=gg.getResults(count)gg.clearResults()local data={}if(count>0)then for i,v in ipairs(result) do v.isUseful=true end for k=1,#SSSJ do local tmp={}local offset=SSSJ[k][1]*4 local num=SSSJ[k][2]for i,v in ipairs(result) do tmp[#tmp+1]={}tmp[#tmp].address=v.address+offset tmp[#tmp].flags=v.flags end tmp=gg.getValues(tmp)for i,v in ipairs(tmp) do if (v.value~=num)then result[i].isUseful=false end end end for i,v in ipairs(result) do if (v.isUseful)then data[#data+1]=v.address end end if data[1]==nil then gg.toast("")else if NCLX[4]~=false then jldz[NCLX[4]]=data KYXG(data,XGSJ,GNM,"")else KYXG(data,XGSJ,GNM,"")end end else gg.toast(GNM.."")end else KYXG(jldz[NCLX[4]],XGSJ,GNM,"")end end

if gg.isVisible(true) 
  then 
    gg.setVisible(false)
  end

function main()
Menu = gg.choice({"✘𝙼𝚊𝚐𝚒𝚌 𝙱𝚞𝚕𝚕𝚎𝚝 𝚅1","✘𝙼𝚊𝚐𝚒𝚌 𝙱𝚞𝚕𝚕𝚎𝚝 𝚅2","✘8 𝚂𝚌𝚘𝚞𝚙𝚎","✘𝙽𝚘 𝚁𝚎𝚌𝚘𝚒𝚕","✘𝚊𝚗𝚝𝚎𝚗𝚊","Exit"}, nil,"𝙼𝚊𝚒𝚗 𝙰𝚌𝚌𝚘𝚞𝚗𝚝 𝚂𝚌𝚛𝚒𝚙𝚝")

if Menu == 1 then F1() end
if Menu == 2 then F2() end
if Menu == 3 then F3() end
if Menu == 4 then F4() end
if Menu == 5 then F5() end
if Menu == 6 then Exit() end
end

function F1()
gg.clearResults()
qmnb = {

{["memory"] =    4 },-----

{["name"] = "搜索到"},

{["value"] =   1031127695 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)

qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到"},

{["value"] =   1025758986 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1035489772 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1042536202 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {
{["memory"] =    4 },-----

{["name"] = " 搜索到 "},

{["value"] =   1038174126 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = "搜索到"},

{["value"] =   1031127695 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)

qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到"},

{["value"] =   1025758986 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1035489772 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1042536202 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {
{["memory"] =    4 },-----

{["name"] = " 搜索到 "},

{["value"] =   1038174126 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = "搜索到"},

{["value"] =   1031127695 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)

qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到"},

{["value"] =   1025758986 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1035489772 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1042536202 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {
{["memory"] =    4 },-----

{["name"] = " 搜索到 "},

{["value"] =   1038174126 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = "搜索到"},

{["value"] =   1031127695 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)

qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到"},

{["value"] =   1025758986 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1035489772 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1042536202 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {
{["memory"] =    4 },-----

{["name"] = " 搜索到 "},

{["value"] =   1038174126 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = "搜索到"},

{["value"] =   1031127695 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)

qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到"},

{["value"] =   1025758986 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1035489772 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {

{["memory"] =    4 },-----

{["name"] = " 搜索到  "},

{["value"] =   1042536202 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
qmnb = {
{["memory"] =    4 },-----

{["name"] = " 搜索到 "},

{["value"] =   1038174126 , ["type"] =    4  },

{["lv"] =257, ["offset"] =  -4, ["type"] = 4},}

qmxg = {

{["value"] =99, ["offset"] =4, ["type"] =  16  },--0.44999998808

}
xqmnb(qmnb)
end

function F3()
gg.setRanges(32)
          SearchWrite({
            {1111490560, 6584},
            {0, 6588},
            {0, 6596}
          }, {
            {
              1084410514,
              6584,
              false
            }
          }, 4)
          gg.clearResults()
          gg.setRanges(32)
          SearchWrite({
            {1110704128, 36264},
            {0, 36256},
            {0, 36268}
          }, {
            {
              1084410514,
              36264,
              false
            }
          }, 4)
          gg.clearResults()
gg.toast("x8 Scoupe〘𝙬𝙚𝙢𝙤𝙙𝙨𝙥𝙧𝙤〙")
end


function F2()
gg.clearResults()
qmnb = {
  {memory = 4},
  {
    name = "◼◻◻◻◻◻◻◻◻◻"
  },
  {value = 0.6899999976158142, type = 16},
  {
    lv = 0.1599999964237213,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◻◻◻◻◻◻◻◻"
  },
  {value = 0.47999998927116394, type = 16},
  {
    lv = 0.09000000357627869,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◻◻◻◻◻◻◻"
  },
  {value = 0.30000001192092896, type = 16},
  {
    lv = 0.05999999865889549,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◻◻◻◻◻◻◻"
  },
  {value = 0.44999998807907104, type = 16},
  {
    lv = 0.03999999910593033,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {name = "◼◼◼◼◼◻◻◻◻◻◻"},
  {value = 0.3400000035762787, type = 16},
  {
    lv = 0.10999999940395355,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◼◼◻◻◻◻◻"
  },
  {value = 0.5400000214576721, type = 16},
  {
    lv = 0.09000000357627869,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◼◼◼◻◻◻◻"
  },
  {value = 0.6899999976158142, type = 16},
  {
    lv = 0.1599999964237213,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◼◼◼◼◻◻◻"
  },
  {value = 0.47999998927116394, type = 16},
  {
    lv = 0.09000000357627869,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◼◼◼◼◼◻◻"
  },
  {value = 0.30000001192092896, type = 16},
  {
    lv = 0.05999999865889549,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {
    name = "◼◼◼◼◼◼◼◼◼◼◻"
  },
  {value = 0.44999998807907104, type = 16},
  {
    lv = 0.03999999910593033,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
qmnb = {
  {memory = 4},
  {name = "◼◼◼◼◼◼◼◼◼◼◼"},
  {value = 0.3400000035762787, type = 16},
  {
    lv = 0.10999999940395355,
    offset = -4,
    type = 16
  }
}
qmxg = {
  {
    value = 99,
    offset = 0,
    type = 16
  }
}
xqmnb(qmnb)
  gg.toast("Magic Bullet By [🌟 BlackMods 🌟]")
end

function F3()
gg.setRanges(32)
          SearchWrite({
            {1111490560, 6584},
            {0, 6588},
            {0, 6596}
          }, {
            {
              1084410514,
              6584,
              false
            }
          }, 4)
          gg.clearResults()
          gg.setRanges(32)
          SearchWrite({
            {1110704128, 36264},
            {0, 36256},
            {0, 36268}
          }, {
            {
              1084410514,
              36264,
              false
            }
          }, 4)
          gg.clearResults()
gg.toast("x8 Scoupe〘Black Mods〙")
end

function F4()
qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = "12.0", type = 16},
    {
      lv = "6.0",
      offset = 12,
      type = 16
    },
    {
      lv = "35.0",
      offset = 28,
      type = 16
    },
    {
      lv = "790.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)

qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = 12, type = 16},
    {
      lv = "6.0",
      offset = 12,
      type = 16
    },
    {
      lv = "35.0",
      offset = 28,
      type = 16
    },
    {
      lv = "830.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)

qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = 14, type = 16},
    {
      lv = "6.0",
      offset = 12,
      type = 16
    },
    {
      lv = "40.0",
      offset = 28,
      type = 16
    },
    {
      lv = "735.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 45, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "60.0",
      offset = 28,
      type = 16
    },
    {
      lv = "300.0",
      offset = 148,
      type = 16
    },
    {
      lv = "15.0",
      offset = 164,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  
  qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = 15, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "25.0",
      offset = 28,
      type = 16
    },
    {
      lv = "300.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "1.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  
qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = "735.0", type = 16},
    {
      lv = "15.0",
      offset = -148,
      type = 16
    },
    {
      lv = "33.0",
      offset = -144,
      type = 16
    },
    {
      lv = "6.0",
      offset = -136,
      type = 16
    },
    {
      lv = "20.0",
      offset = -108,
      type = 16
    },
    {
      lv = "10.0",
      offset = -96,
      type = 16
    },
    {
      lv = "10.0",
      offset = -92,
      type = 16
    },
    {
      lv = "10.0",
      offset = -88,
      type = 16
    },
    {
      lv = "4.0",
      offset = 16,
      type = 16
    },
    {
      lv = "4.0",
      offset = 24,
      type = 16
    },
    {
      lv = "1.0",
      offset = 160,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = -148,
      type = 16
    },
    {
      value = 0,
      offset = -144,
      type = 16
    },
    {
      value = 0,
      offset = -136,
      type = 16
    },
    {
      value = 0,
      offset = -108,
      type = 16
    },
    {
      value = 0,
      offset = -96,
      type = 16
    },
    {
      value = 0,
      offset = -92,
      type = 16
    },
    {
      value = 0,
      offset = -88,
      type = 16
    },
    {
      value = 9999,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 16,
      type = 16
    },
    {
      value = 0,
      offset = 24,
      type = 16
    },
    {
      value = 0,
      offset = 160,
      type = 16
    }
  }
  xqmnb(qmnb)
  
qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = 16, type = 16},
    {
      lv = "2.0",
      offset = 12,
      type = 16
    },
    {
      lv = "30.0",
      offset = 28,
      type = 16
    },
    {
      lv = "320.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "5.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  
  qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 15, type = 16},
    {
      lv = "6.0",
      offset = 12,
      type = 16
    },
    {
      lv = "30.0",
      offset = 28,
      type = 16
    },
    {
      lv = "710.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  
qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 15, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "10.0",
      offset = 40,
      type = 16
    },
    {
      lv = "4.0",
      offset = 112,
      type = 16
    },
    {
      lv = "4.0",
      offset = 116,
      type = 16
    },
    {
      lv = "2.799999952316284",
      offset = 120,
      type = 16
    },
    {
      lv = "40.0",
      offset = 148,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 40,
      type = 16
    },
    {
      value = 0,
      offset = 112,
      type = 16
    },
    {
      value = 0,
      offset = 116,
      type = 16
    },
    {
      value = 9999,
      offset = 148,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = 24, type = 16},
    {
      lv = "24.0",
      offset = 12,
      type = 16
    },
    {
      lv = "10.0",
      offset = 40,
      type = 16
    },
    {
      lv = "4.0",
      offset = 112,
      type = 16
    },
    {
      lv = "4.0",
      offset = 116,
      type = 16
    },
    {
      lv = "2.799999952316284",
      offset = 120,
      type = 16
    },
    {
      lv = "25.0",
      offset = 148,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 40,
      type = 16
    },
    {
      value = 0,
      offset = 112,
      type = 16
    },
    {
      value = 0,
      offset = 116,
      type = 16
    },
    {
      value = 9999,
      offset = 148,
      type = 16
    }
  }
  xqmnb(qmnb)
    qmnb = {
    {memory = 32},
    {name = "带镜路"},
    {value = "480.0", type = 16},
    {
      lv = "20.0",
      offset = -148,
      type = 16
    },
    {
      lv = "40.0",
      offset = -144,
      type = 16
    },
    {
      lv = "6.0",
      offset = -136,
      type = 16
    },
    {
      lv = "60.0",
      offset = -120,
      type = 16
    },
    {
      lv = "0.5",
      offset = -100,
      type = 16
    },
    {
      lv = "4.0",
      offset = 16,
      type = 16
    },
    {
      lv = "4.0",
      offset = 24,
      type = 16
    },
    {
      lv = "1.0",
      offset = 160,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = -148,
      type = 16
    },
    {
      value = 0,
      offset = -144,
      type = 16
    },
    {
      value = 0,
      offset = -136,
      type = 16
    },
    {
      value = 0,
      offset = -120,
      type = 16
    },
    {
      value = 0,
      offset = -100,
      type = 16
    },
    {
      value = 9999,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 16,
      type = 16
    },
    {
      value = 0,
      offset = 24,
      type = 16
    },
    {
      value = 0,
      offset = 160,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 45, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "60.0",
      offset = 28,
      type = 16
    },
    {
      lv = "300.0",
      offset = 148,
      type = 16
    },
    {
      lv = "13.0",
      offset = 164,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 14, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "25.0",
      offset = 28,
      type = 16
    },
    {
      lv = "360.0",
      offset = 148,
      type = 16
    },
    {
      lv = "4.0",
      offset = 164,
      type = 16
    },
    {
      lv = "4.0",
      offset = 172,
      type = 16
    },
    {
      lv = "5.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 172,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
  qmnb = {
    {memory = 32},
    {
      name = "带镜路"
    },
    {value = 45, type = 16},
    {
      lv = "3.0",
      offset = 12,
      type = 16
    },
    {
      lv = "60.0",
      offset = 28,
      type = 16
    },
    {
      lv = "300.0",
      offset = 148,
      type = 16
    },
    {
      lv = "15.0",
      offset = 164,
      type = 16
    },
    {
      lv = "8.0",
      offset = 192,
      type = 16
    }
  }
  qmxg = {
    {
      value = 0,
      offset = 0,
      type = 16
    },
    {
      value = 0,
      offset = 12,
      type = 16
    },
    {
      value = 0,
      offset = 28,
      type = 16
    },
    {
      value = 99999,
      offset = 148,
      type = 16
    },
    {
      value = 0,
      offset = 164,
      type = 16
    },
    {
      value = 0,
      offset = 192,
      type = 16
    }
  }
  xqmnb(qmnb)
end

function F5()
gg.clearResults()
    gg.setRanges(4)
    gg.searchNumber('-0.9855342507362366', gg.REGION_C_BSS, false, gg.SIGN_FUZZY_EQUAL, 0, -1)
    gg.getResults(999)
    gg.editAll('-999', gg.REGION_C_BSS)
    gg.clearResults()
    gg.clearList()
end

function Exit()
gg.clearResults()
os.exit()
end

main()

while(true)
do
  while gg.isVisible(true)
    do
      gg.setVisible(false)
      main()
    end
end
