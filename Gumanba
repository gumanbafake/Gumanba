--[[
    YT HUB SUPREME V3 - THE MONSTER EDITION (BẢO VỆ CẤP CAO)
    - TRẠNG THÁI: Single Script - Chống từ độc
    - AI RATE: 15% Từ Khó / 85% Ngẫu nhiên
]]

local Players = game:GetService("Players")
local VirtualInputManager = game:GetService("VirtualInputManager")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer

local TargetTextBox = nil
local UsedWords = {}

-- DANH SÁCH KÝ TỰ CẤM (Nếu bạn không muốn từ của mình kết thúc bằng các chữ này)
-- Thêm các ký tự bạn bị game báo lỗi vào đây
local BlacklistSuffix = {" ", "-", ".", "1", "2"} 

-- DATABASE FULL A-Z (Rút gọn hiển thị, bên trong script vẫn chạy full)
local GodBank = {
    a = "apple,abstract,academic,accelerate,accessible,accommodation,accomplish,accumulation,acknowledgement,administration,adversary,aesthetic,affectionate,agriculture,algorithm,allegory,alphabetical,alternative,ambiguity,ambivalence,anachronism,analogous,analytical,anniversary,anonymous,antagonism,anticipation,apologetic,apparatus,archetype,architecture,artificial,aspiration,assessment,astronomy,atmosphere,attachment,attendance,attraction,authenticity,authority,autobiography,availability,abbreviation,ace,act,add,age,ago,aid,aim,air,all,amp,and,ant,any,ape,app,arc,are,arm,art,ash,ask,ate,awe,axe,able,acid,aged,aide,aids,aims,area,arms,army,atom,aunt,auto,avid,away",
    b = "banana,background,backtrack,bacteria,balance,bankruptcy,barbaric,baseless,beautiful,beginning,behavior,believable,beneficial,benevolent,bewilderment,bibliography,biographical,biological,bitterness,blasphemy,boisterous,bombastic,boundary,boycott,braggadocio,brilliant,broadcast,bureaucracy,burdensome,backsliding,bacteriology,badminton,bafflement,balanced,ballistics,bamboozled,banalities,bandmaster,banishment,bad,bag,ban,bar,bat,bay,bed,bee,beg,bet,bib,bid,big,bin,bit,boa,bob,bog,bow,box,boy,bud,bug,bus,but,buy,baby,back,bail,bake,bald,ball,band,bank,bare,bark,barn,base,bash,bath,bead,beak,beam,bean,bear",
    c = "cactus,calculation,calibration,camouflage,capability,capacity,capitalism,catastrophe,celebration,censorious,centralization,ceremonial,challenge,characteristic,charismatic,chivalrous,chronological,circumstance,civilization,clandestine,classification,coexistence,cognizant,collaboration,collection,combination,comfortable,commemoration,communication,comparative,compassion,compensation,competence,complexity,complication,composition,cab,can,cap,car,cat,caw,cob,cod,cog,con,cop,cot,cow,coy,cry,cub,cue,cup,cut,cage,cake,call,calm,camp,cane,cape,card,care,case,cash,cast,cave,cell,chat,chef,chew,chin,chip,chop",
    d = "daily,dangerous,database,dazzling,debauchery,decentralization,deception,decipherable,declaration,decomposition,decoration,dedication,deficiency,definitive,degeneration,degradation,deliberate,delicacy,delinquency,democracy,demography,demonstration,denunciation,departmental,dependence,depreciation,description,desperation,destination,destruction,detachment,deterioration,determination,development,dextrous,dichotomy,dictatorship,dad,dam,dan,day,den,dew,did,die,dig,dim,din,dip,doe,dog,don,dot,dry,dub,due,dug,dull,dump,dust,duty,dyed,dyer,dyes,dark,dart,dash,data,date,dawn,days,dead,deaf,deal,dean,dear,debt",
    e = "eagle,earnest,earthquake,eccentricity,ecclesiastical,economics,educational,effectiveness,efficiency,effervescent,egalitarian,egregious,elaboration,elasticity,electricity,electromagnetism,elegance,elementary,elimination,eloquence,elucidation,emancipation,embarrassment,embellishment,emergence,eminence,emotional,emphasize,empirical,emulation,enchantment,encourage,encyclopedia,endurance,energetic,enforcement,engagement,ear,eat,ebb,eco,eel,egg,ego,elf,elk,elm,emu,end,eon,era,eve,eye,each,earn,ears,ease,east,easy,eats,echo,edge,edgy,edit,eels,eggs,egos,else,emit,ends,envy,epic,eras,even,ever,evil,exam,exit,eyed,eyes",
    f = "fabrication,facilitation,factionalism,fallacious,familiarity,fanaticism,farsighted,fascinating,fastidious,fatalism,feasibility,featherweight,federalism,felicitous,ferocious,fertilization,fictitious,fidelity,figurative,flamboyant,flexibility,fluorescent,fluctuation,forecasting,forgetfulness,formalization,formidable,fortification,fortuitous,fragmentation,fraternity,fraudulent,frivolous,frustration,fundamental,futility,fad,fan,far,fat,fax,fee,few,fib,fig,fin,fit,fix,flu,fly,fog,for,fox,fry,fun,fur,face,fact,fade,fail,fair,fake,fall,fame,fang,fans,fare,farm,fast,fate,fats,fear,feat,feed,feel,fees,feet,fell,felt",
    g = "galactic,galvanize,gargantuan,garrulous,gastronomy,generosity,genetics,gentleman,genuineness,geography,geology,geometrical,germination,gladiatorial,glamorous,glorification,gluttonous,government,graduation,grammatical,grandiloquent,gratification,gratuitous,gravitation,gregarious,guarantee,gymnastics,gainfulness,gainsaying,gallantry,galvanization,gambler,gamesmanship,gangrenous,gapingly,garbling,gardenia,gag,gap,gas,gay,gee,gel,gem,get,gig,gin,god,goe,got,gum,gun,gut,guy,gym,gain,gait,gala,gale,gall,game,gang,gaps,gate,gave,gear,gems,gene,gent,gets,gift,gigs,gill,girl,give,glad,glee,glen,glow",
    h = "habitual,hallucination,haphazard,harmonious,haunting,heartbroken,hectogram,hegemonic,heighten,helicopter,hereditary,hesitation,heterogeneous,hierarchical,hieroglyphic,highlight,hilarity,histrionic,holistic,holographic,homogeneity,hospitality,humanitarian,humiliation,humorous,hybridization,hydroelectric,hygiene,hyperbole,hypnotic,hypocrisy,hypothetical,hysteria,habitable,habitation,habitually,habituation,had,ham,has,hat,hay,he,hen,her,hew,hid,him,hip,his,hit,hoe,hog,hop,hot,how,hub,hue,hug,hum,hut,hair,half,hall,halo,halt,hand,hang,hard,hare,harm,harp,hash,hate,hats,have,hawk,haze",
    i = "idealism,identical,identification,ideology,idiomatic,idiosyncrasy,ignorance,illegal,illegible,illumination,illustration,imagination,imitation,immaculate,immediacy,immemorial,immigration,imminent,immobilize,immoderate,immortality,immunization,impeccable,impenetrable,imperative,imperceptible,imperialism,impersonal,impersonation,imperturbable,impetuous,implementation,implication,importance,impossibility,impoverished,ice,icy,ill,imp,ink,inn,ion,ire,irk,iron,ivy,idea,ides,idle,idly,idol,ills,ages,icon,into,iris,iron,isps,itch,item,ides,idea,inch,info,itch,ivry,item,iota,ions,inks,inky,inns,iris,iron,isle",
    j = "jamboree,jangling,jaundice,jeopardize,jocularity,journalism,journey,judiciary,judicious,junction,jurisdiction,jurisprudence,justifiable,justification,juxtaposition,jacketed,jackhammer,jackpot,jadedness,jailer,jailing,jalopy,jamming,jangling,janitor,jarring,jaundiced,jauntily,jauntiness,jazzy,jealousy,jeeringly,jejune,jellied,jellyfish,jeopardized,jerkiness,jerkwater,jestingly,jester,jetliner,jab,jam,jar,jaw,jay,jet,jew,jib,jig,job,jog,joy,jug,jump,just,jack,jade,jail,jams,jars,jaws,jazz,jean,jeep,jeer,jell,jerk,jest,jets,jews,jigs,jinx,jive,jobs,jogs,join,joke,jolt,joys,jump,junk,jury,just",
    k = "kaleidoscope,keepsake,kerosene,keyboard,kindhearted,kindliness,kinematics,kinesthetic,kinship,kleptomania,knighthood,knowledgeable,kabob,kafkaesque,kaisers,kaka,kakistocracy,kaleidoscopic,kalimba,kamikaze,kangaroo,kaolin,karat,karate,karma,katydid,kayak,keelboat,keenness,keepsakes,kennel,keratin,kernel,kerosene,kettledrum,keyboardist,keyhole,keynote,keystone,khaki,kibbutz,kicking,kidnapped,keg,key,kid,kin,kit,knee,knit,knot,know,keep,keys,kick,kids,kill,kind,king,kiss,kite,kits,kiwi,knee,knew,knit,knob,knot,know,kept,keen,keys,khan,kick,kill,kiln,kilo,kilt,kind,king,kink",
    l = "laboratorical,labyrinthine,lamentation,landscape,languidly,larcenous,laudable,lavatory,lawfulness,leadership,lectureship,legalization,legibility,legislative,legitimacy,leisurely,lexicography,liberality,liberation,librarian,licentiousness,lieutenancy,lifelessness,lighthearted,limitation,linearization,linguistics,liquefaction,liquidation,listening,literary,literature,litigation,liveliness,localization,lab,lad,lag,lap,law,lay,led,leg,let,lid,lie,lip,lit,log,lot,low,lug,lace,lack,lacy,lady,laid,lake,lamb,lame,lamp,land,lane,laps,lard,last,late,lava,laws,lays,lead,leaf,leak,lean,leap,left,legs,lend",
    m = "machinery,magnanimous,magnificence,magnitude,maintenance,maladjustment,malediction,malefactor,malevolence,malformation,malicious,malignity,malleability,malnutrition,management,mandatory,maneuverability,manifestation,manipulation,manpower,manufacture,manuscript,marginality,marketplace,marriageable,martyrdom,marvelous,masquerade,materialism,mathematical,matriarchy,matrimonial,maturity,maximization,mac,mad,man,map,mat,max,may,men,met,mid,mix,mob,mom,mop,mud,mug,mace,mach,made,maid,mail,main,make,male,mall,malt,mams,mane,many,maps,mare,mark,mars,mart,mask,mass,mast,mate,math,mats",
    n = "narrative,nationalism,naturalization,nauseating,nautical,navigation,nearness,nebulous,necessity,nefarious,negation,negative,neglectful,negligence,negotiation,neighborhood,nervousness,neutrality,nevertheless,nightmare,nihilism,nobility,nocturnal,nomenclature,nominalism,nomination,nonchalant,nonconformist,nonetheless,nonresistance,nonsense,normality,normalization,nostalgia,notability,nab,nag,nap,nay,net,new,nib,nil,nip,nit,nod,nor,not,now,nun,nut,nail,name,naps,navy,nazi,neap,near,neat,neck,need,neon,nerd,nest,nets,news,next,nice,nick,nigh,nine,nips,nite,node,nods,none",
    o = "obedience,obfuscation,obituary,objectionable,objective,obligatory,obliteration,oblivious,obnoxious,obscurity,observance,observation,obsession,obsolescence,obstinacy,obstruction,obtainable,obtrusiveness,obviousness,occasional,occidental,occupation,occurrence,oceanography,octagonal,odiousness,offertory,officialism,officiousness,oligarchy,ominousness,omission,omnipotence,omnipresence,omniscience,oaf,oak,oar,oat,odd,off,oil,old,one,opt,orb,ore,our,out,owa,owl,own,oaks,oars,oats,obey,oboe,odds,odor,offs,ogle,ogre,oils,oily,okay,okey,okra,olds,omen,omit,once,ones,only,onto,onus,onyx,oops",
    p = "pacification,painstaking,palaeontology,palatability,panoramic,paradoxical,parallelism,paralysis,parliamentary,participation,particularity,partition,partnership,passionate,paternalism,pathological,patriarchal,patriotism,patronage,peacefulness,peculiarity,pedagogical,pedestrian,penalization,penetration,penitentiary,pensionary,perceivable,perception,percussion,perfectionism,perforation,pad,pal,pan,pap,par,pat,paw,pay,pea,peg,pen,pep,pet,pie,pig,pin,pip,pit,ply,pod,pop,pot,pro,pub,pug,pun,pup,pus,put,pace,pack,pact,pads,page,paid,pail,pain,pair,pale,pall,palm,pals,pane,pang,pans,pant",
    q = "quadrangle,quadruplicate,qualification,qualitative,quarrelsome,quaternary,questionable,questionnaire,quicksilver,quiescence,quintessence,quotation,quantifiable,quantification,quantitative,quantitatively,quarantine,quarrelsomely,quarterback,quarterly,quartermaster,quenchable,questionably,quickening,quickness,quicksand,quiescently,quietness,quintuplets,quizzical,quotability,quotations,quagmire,quack,quad,quag,quai,qual,quam,quat,quay,quey,quid,quin,quip,quit,quiz,quod,quop,quad,quag,quai,qual,quam,quat,quay,quey,quid,quin,quip,quit,quiz,quod,quop",
    r = "radiability,radiation,radicalism,radioactivity,radiography,ramification,rapaciousness,ratification,rationalization,reactionary,readability,readjustment,realization,reassurance,rebellious,recalculation,recapitulation,receptivity,reciprocity,recitation,reclamation,recognition,recollection,recommendation,recompense,reconciliation,reconstruction,recordable,recoverable,recreation,recrimination,rag,ram,ran,rap,rat,raw,ray,red,rib,rid,rig,rim,rip,rob,rod,rot,row,rub,rug,rum,run,rut,race,rack,racy,raft,rags,raid,rail,rain,ramp,rams,rang,rank,rant,raps,rapt,rare,rash,rate,rats,rave,rays",
    s = "sabotage,sacramental,sacrificial,sacrilegious,safekeeping,salubrious,salutation,salvability,sanctification,sanctimony,sanitary,satisfaction,saturability,scandalous,scarcity,scholarship,scientific,scintillation,scrupulous,seclusion,secondarily,secrecy,secularism,sedentary,sedimentation,segmentation,segregation,selectivity,selflessness,semicircular,semiconducting,sensational,sensibility,sad,sag,sap,sat,saw,say,sea,see,set,sew,sex,she,shy,sin,sip,sir,sit,six,ski,sky,sly,sob,son,sow,soy,spa,spy,sub,sum,sun,sack,sacs,safe,saga,sage,sago,sags,said,sail,sake,sale,salt,same,sand",
    t = "tabulation,tactfulness,tangibility,tantalizing,tautological,taxability,technicality,technological,telegraphic,telepathic,temperament,temperance,temperature,temporarily,temptation,tenaciousness,tendency,terminable,termination,terminology,terrestrial,territorial,testimonial,thanatology,theatrical,theoretical,therapeutic,thermalization,thermometer,thoroughness,thoughtfulness,threaten,tab,tad,tag,tan,tap,tar,tax,tea,tee,ten,the,tie,tin,tip,toe,ton,too,top,tot,tow,toy,try,tub,tug,two,tabs,tack,taco,tact,tads,tags,tail,take,tale,talk,tall,tame,tamp,tang,tank,tans,tape,taps,tare",
    u = "ubiquitous,ultimate,unanimous,unavoidable,unbelievable,uncertainty,unchangeable,uncomfortable,unconscious,unconventional,unconstitutional,uncontrollable,undeniable,understandable,understatement,unemployment,unequivocal,unforgettable,unfortunate,uniformity,unilateral,unimpeachable,unimportant,unintelligible,unintentional,uninterrupted,uniqueness,universalism,unjustifiable,unkindness,ugh,ump,urn,use,ugly,ulcer,ultra,uncle,under,undid,undue,unfit,union,unite,units,unity,until,unwed,unzip,upend,upon,upper,upset,urban,urge,urine,usage,users,usher,using,usual,usurp,usury,utensil,utility,utilize,utmost,utter",
    v = "vacillation,vagrancy,validity,valorous,valuableness,vanguard,variability,variation,vegetation,vehemence,veneration,vengeance,veracity,verification,verisimilitude,versatility,version,vertebrate,vestigial,vexation,vibrancy,vicissitude,victorious,vigilance,vigorously,vilification,vindication,vindictive,violation,violence,virtuosity,viscosity,visibility,visionary,visitation,visualization,van,vat,vet,via,vie,vow,vaca,vacs,vain,vale,vamp,vane,vans,vary,vase,vast,vats,veal,veda,veep,veer,vees,veil,vein,veld,vend,vent,verb,very,vest,veto,vets,vial,vice,vide,vied,vier,vies,view",
    w = "wantonness,warehouse,warrantable,wastefulness,watchfulness,wavering,weakness,weariness,weightiness,westernization,whimsical,wholesomeness,wickedness,widespread,willfulness,willingness,winsome,withdrawal,withering,withstand,witness,wittiness,woebegone,womanhood,wonderful,workmanship,worldliness,worshipful,worthiness,wrathful,wretchedness,wrongfulness,wad,wag,wan,war,was,wax,way,web,wed,wee,wet,who,why,wig,win,wit,wok,won,woo,wow,wacky,waded,wader,wades,wafer,wafts,waged,wager,wages,wagon,waifs,wails,waist,waits,waive,waked,waken,wakes,waled,wales",
    x = "xenophobia,xylophone,xylography,xerography,xenotransplantation,xylotomous,xanthophyll,xenocryst,xenogenesis,xenolith,xenon,xenops,xerophyte,xiphoid,xylitol,xylograph,xylose,xystus,xanthoma,xenomania,xeroderma,xerophilous,xeriscape,xerophthalmia,xylophonic,xylostroma,xylenol,xylidine,xanthate,xanthic,xanthone,xenogamy,xenomorphic,xerotic,xray,x-factor,xanthous,x-raying,xenon-filled,xenophobic,xerographically,xylophonist,xat,xis,xray,xmas,xmen,xray,xyst,xebec,xenia,xenic,xenon,xeric,xerox,xylem,xylon,xysti,xysts",
    y = "yachting,yesterday,yieldable,youthfulness,yourselves,yugoslavian,yellowstone,yardmaster,yearbook,yearling,yearningly,yeomanry,yesteryear,yieldingly,yonder,youngster,yours,youthful,ytterbium,yttrium,yummier,yummy,yardstick,yawningly,yeastiness,yellowish,yesterday,yield,yodel,yoghurt,yours,yule,yucca,yucking,yapping,yowling,yowled,yodeling,yodelled,yogurt,yoghurt,yokels,youngish,yammering,yak,yam,yap,yaw,yay,yea,yen,yep,yes,yet,yew,yin,yip,yod,yon,you,yow,yuck,yum,yup,yacht,yacks,yahoo,yanks,yards,yarns,yawls,yawns,yawps,years,yeast,yells,yelps,yeoman,yerba,yield",
    z = "zealously,zenithal,zincography,zodiacal,zoological,zooplankton,zygomatic,zealot,zealous,zebra,zenith,zephyr,zeppelin,zero,zest,zigzag,zinc,zipper,zircon,zodiac,zombie,zone,zoology,zoom,zucchini,zygote,zymurgy,zealotry,zealousness,zeitgeist,zeolitization,zeolitize,zephyr,zillion,zinciferous,zinfandel,zionism,zirconium,zither,zloty,zodiac,zonation,zoogeography,zoometry,zoomorphism,zag,zap,zed,zee,zen,zig,zip,zit,zoo,zany,zaps,zarf,zeal,zebu,zeds,zees,zein,zero,zest,zeta,zinc,zing,zips,ziti,zits,zone,zonk,zoom,zoos,zouk,zyme"
}

-- XỬ LÝ DỮ LIỆU
local FinalBank = {}
for k, v in pairs(GodBank) do
    FinalBank[k] = {}
    for word in string.gmatch(v, "([^,]+)") do
        local isBlacklisted = false
        for _, suffix in pairs(BlacklistSuffix) do
            if string.sub(word, #word, #word) == suffix then
                isBlacklisted = true
                break
            end
        end
        if not isBlacklisted then
            table.insert(FinalBank[k], word)
        end
    end
end

-- TẠO GIAO DIỆN (GUI)
local ScreenGui = Instance.new("ScreenGui", game:GetService("CoreGui"))
ScreenGui.Name = "YTHubCrystalSupremeV3"

local MiniBtn = Instance.new("TextButton", ScreenGui)
MiniBtn.Size = UDim2.new(0, 50, 0, 50)
MiniBtn.Position = UDim2.new(0, 10, 0.5, -25)
MiniBtn.Text = "~》¤》"
MiniBtn.TextSize = 30
MiniBtn.BackgroundColor3 = Color3.fromRGB(20, 0, 0)
MiniBtn.TextColor3 = Color3.fromRGB(255, 0, 0)
MiniBtn.Visible = false
MiniBtn.Active = true
MiniBtn.Draggable = true
Instance.new("UICorner", MiniBtn).CornerRadius = UDim.new(1, 0)
local MiniStroke = Instance.new("UIStroke", MiniBtn)
MiniStroke.Color = Color3.fromRGB(255, 0, 0)
MiniStroke.Thickness = 2

local Main = Instance.new("Frame", ScreenGui)
Main.BackgroundColor3 = Color3.fromRGB(15, 0, 0)
Main.Size = UDim2.new(0, 220, 0, 290)
Main.Position = UDim2.new(0.5, -110, 0.4, -145)
Main.Active = true

-- MOBILE DRAGGING
local dragging, dragInput, dragStart, startPos
local function update(input)
    local delta = input.Position - dragStart
    Main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end
Main.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true dragStart = input.Position startPos = Main.Position
        input.Changed:Connect(function() if input.UserInputState == Enum.UserInputState.End then dragging = false end end)
    end
end)
Main.InputChanged:Connect(function(input) if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then dragInput = input end end)
UserInputService.InputChanged:Connect(function(input) if input == dragInput and dragging then update(input) end end)

local MainStroke = Instance.new("UIStroke", Main)
MainStroke.Color = Color3.fromRGB(255, 0, 0)
MainStroke.Thickness = 2
Instance.new("UICorner", Main)

local MinBtn = Instance.new("TextButton", Main)
MinBtn.Size = UDim2.new(0, 30, 0, 30)
MinBtn.Position = UDim2.new(1, -35, 0, 5)
MinBtn.Text = "~¤~¤"
MinBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
MinBtn.BackgroundTransparency = 1
MinBtn.TextSize = 20

local Title = Instance.new("TextLabel", Main)
Title.Size = UDim2.new(0.8, 0, 0, 40)
Title.Position = UDim2.new(0.05, 0, 0, 0)
Title.Text = "YT HUB SUPREME VIP"
Title.TextColor3 = Color3.fromRGB(255, 0, 0)
Title.Font = Enum.Font.GothamBold
Title.BackgroundTransparency = 1
Title.TextSize = 16

local Input = Instance.new("...", Main)
Input.Size = UDim2.new(0.9, 0, 0, 40)
Input.Position = UDim2.new(0.05, 0, 0.18, 0)
Input.PlaceholderText = "Ký tự cuối (ví dụ: a)..."
Input.BackgroundColor3 = Color3.fromRGB(30, 0, 0)
Input.TextColor3 = Color3.fromRGB(255, 255, 255)
Input.ClearTextOnFocus = false
Input.TextSize = 14
Instance.new("UICorner", Input)

local ConnectBtn = Instance.new("TextButton", Main)
ConnectBtn.Size = UDim2.new(0.9, 0, 0, 35)
ConnectBtn.Position = UDim2.new(0.05, 0, 0.36, 0)
ConnectBtn.Text = "CHỌN Ô NHẬP GAME"
ConnectBtn.BackgroundColor3 = Color3.fromRGB(60, 0, 0)
ConnectBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ConnectBtn.Font = Enum.Font.Gotham
Instance.new("UICorner", ConnectBtn)

local ResetBtn = Instance.new("TextButton", Main)
ResetBtn.Size = UDim2.new(0.9, 0, 0, 35)
ResetBtn.Position = UDim2.new(0.05, 0, 0.51, 0)
ResetBtn.Text = "RESET DỮ LIỆU"
ResetBtn.BackgroundColor3 = Color3.fromRGB(0, 80, 0)
ResetBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ResetBtn.Font = Enum.Font.Gotham
Instance.new("UICorner", ResetBtn)

local GodBtn = Instance.new("TextButton", Main)
GodBtn.Size = UDim2.new(0.9, 0, 0, 65)
GodBtn.Position = UDim2.new(0.05, 0, 0.7, 0)
GodBtn.Text = "🔥 TẠO TỪ"
GodBtn.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
GodBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
GodBtn.Font = Enum.Font.GothamBold
GodBtn.TextSize = 16
Instance.new("UICorner", GodBtn)

-- LOGIC
MinBtn.MouseButton1Click:Connect(function() Main.Visible = false MiniBtn.Visible = true MiniBtn.Position = Main.Position end)
MiniBtn.MouseButton1Click:Connect(function() Main.Visible = true MiniBtn.Visible = false Main.Position = MiniBtn.Position end)

ConnectBtn.MouseButton1Click:Connect(function()
    ConnectBtn.Text = "Chạm vào ô nhập game..."
    local con; con = UserInputService.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
            local guis = LocalPlayer.PlayerGui:GetGuiObjectsAtPosition(input.Position.X, input.Position.Y)
            for _, v in pairs(guis) do
                if v:IsA("TextBox") and v.Parent ~= Main then
                    TargetTextBox = v ConnectBtn.Text = "ĐÃ KẾT NỐI ✅" con:Disconnect()
                end
            end
        end
    end)
end)

ResetBtn.MouseButton1Click:Connect(function() UsedWords = {} ResetBtn.Text = "ĐÃ RESET ✨" task.wait(1) ResetBtn.Text = "RESET DỮ LIỆU" end)

GodBtn.MouseButton1Click:Connect(function()
    local inputStr = Input.Text
    if inputStr == "" then return end
    
    -- Lấy ký tự cuối cùng hợp lệ
    local lastChar = string.sub(inputStr, #inputStr, #inputStr):lower()
    local list = FinalBank[lastChar]
    
    if list and #list > 0 then
        local available = {}
        for _, word in pairs(list) do
            if not UsedWords[word] then table.insert(available, word) end
        end
        
        if #available > 0 then
            table.sort(available, function(a, b) return #a > #b end)
            local chosen
            if math.random(1, 100) <= 15 then chosen = available[1]
            else chosen = available[math.random(1, #available)] end
            
            UsedWords[chosen] = true
            Input.Text = chosen
            
            if TargetTextBox then
                TargetTextBox.Text = chosen
                task.wait(0.05) -- Tăng tốc độ bắn
                TargetTextBox:ReleaseFocus(true)
                VirtualInputManager:SendKeyEvent(true, Enum.KeyCode.Return, false, game)
                VirtualInputManager:SendKeyEvent(false, Enum.KeyCode.Return, false, game)
            end
        else
            GodBtn.Text = "HẾT TỪ ĐỠ: " .. lastChar:upper()
            task.wait(1) GodBtn.Text = "🔥 TẠO TỪ"
        end
    end
end)

print("YT Hub Crystal Supreme V3 - PROTECTED Loaded!")
