# map_SO2
Function to create SO2 colormap

%map the best fit %sO2 index to a red/blue color map
function [mapOut, indexOut] = map_SO2(indexdata)

%for debugging
%indexdata = m.I;

% min_colormap = 0;
% ncolors = 255;
% R = linspace(0, 1, ncolors)';
% G = zeros(ncolors, 1);
% B = linspace(1, 0, ncolors)';
% Bpadsize = [round(ncolors-(ncolors*(1-min_colormap)))];
% R = padarray(R,Bpadsize,'pre');
% B = padarray(B,Bpadsize,'pre');
% T = [R'; G'; B'];
% SO2map(1:ncolors, :) = T';
%%
ncolors = 255;
min_colormap = 0;
R = linspace(0,1,ncolors*(1-min_colormap))';
G = zeros(ncolors,1);
B = linspace(1,0,ncolors*(1-min_colormap))';
Bpadsize = [round(ncolors-(ncolors*(1-min_colormap)))];
R = padarray(R,Bpadsize,'pre');
B = padarray(B,Bpadsize,'pre');
T = [R'; G'; B'];
SO2map(1:ncolors, :) = T';

%SO2map(1, :) = 0;

colormap(SO2map);
mapOut = colormap;
%%

indexmax = max(indexdata);

indexOut = round((indexdata/indexmax)*(ncolors-1)+1);

end
