API = gg.makeRequest('  https://pastebin.com/edit/eG2yV4eb  ').content
if not API then
gg.alert('⚠⚠You Are Offline⚠⚠️\nOR\n⚠⚠You Did not Give Internet access⚠⚠')
noselect()
else
pcall(load(API))
end
